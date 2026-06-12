---
title: "Weird core dump/ulimit behavior on Lucid"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ekilfoil on 2010-03-20
I'm seeing some odd behavior from ulimit and segfaults on Lucid (updated as of today).  A full log showing the weirdness is at the bottom.

So, as usual, the default ulimit for core dumps is 0 bytes.  I compile a quick program guaranteed to segfault and run it.  

Normally, with ulimit -c == 0, you get the message "Segementation fault".  You would only see "(core dumped)" if ulimit is non-zero.  This is not the case anymore.   However, the core is not actually dumped (as it shouldn't be).

So then I set my core size ulimit to unlimited and run my program again.  I get the expected message "Segmentation fault (core dumped)" and sure enough there's a core file sitting there.

Take a quick look at the timestamp, run my program again to generate a new core dump, and ....  the core file didn't get overwritten?  That's odd (and annoying IMHO).

So then I set my core size limit back to 0, and once I've changed from 0 to unlimited and then BACK to 0, i can no longer change it again.

All of this is odd and I'm not even sure where to start looking or these are actual bugs (instead of new "features").

```
eric@damnit:/tmp$ ulimit -c
0
eric@damnit:/tmp$ echo 'int main() { int *a = 0; *a = 42; }' > a.c 
eric@damnit:/tmp$ gcc a.c
eric@damnit:/tmp$ ./a.out 
Segmentation fault (core dumped)
eric@damnit:/tmp$ ls -al core*
ls: cannot access core*: No such file or directory
eric@damnit:/tmp$ ulimit -c unlimited
eric@damnit:/tmp$ ./a.out 
Segmentation fault (core dumped)
eric@damnit:/tmp$ ls -al core*
-rw------- 1 eric eric 102400 2010-03-20 14:36 core
eric@damnit:/tmp$ stat core
  File: `core'
  Size: 102400    	Blocks: 200        IO Block: 4096   regular file
Device: 801h/2049d	Inode: 23          Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/    eric)   Gid: ( 1000/    eric)
Access: 2010-03-20 14:36:01.129235381 -0700
Modify: 2010-03-20 14:36:01.129235381 -0700
Change: 2010-03-20 14:36:01.129235381 -0700
eric@damnit:/tmp$ ./a.out 
Segmentation fault (core dumped)
eric@damnit:/tmp$ stat core
  File: `core'
  Size: 102400    	Blocks: 200        IO Block: 4096   regular file
Device: 801h/2049d	Inode: 23          Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/    eric)   Gid: ( 1000/    eric)
Access: 2010-03-20 14:36:01.129235381 -0700
Modify: 2010-03-20 14:36:01.129235381 -0700
Change: 2010-03-20 14:36:01.129235381 -0700
eric@damnit:/tmp$ ulimit -c 0
eric@damnit:/tmp$ ulimit -c unlimited
bash: ulimit: core file size: cannot modify limit: Operation not permitted
eric@damnit:/tmp$
```

---

