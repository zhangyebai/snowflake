### Java版本SnowFlake实现

```
    @Test
    public void testSnowFlakeId(){
        final SyncSnowFlake asf = new SyncSnowFlake(1);
        long start = System.currentTimeMillis();
        IntStream.range(0, 10000000).parallel().forEach(idx -> asf.syncNextId());
        long end = System.currentTimeMillis();
        System.out.println("p1 = " + (end - start));
        IntStream.range(0, 10000000).parallel().forEach(idx -> asf.nextId());
        start = System.currentTimeMillis();
        System.out.println("p2 = " + (start - end));
    }

```
```
p1 = 2596
p2 = 2446
```