---
title: "can not boot in Ubuntu 14"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by chuchi on 2015-10-28
Hi there!

After I ran the the  command
```

sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0

```

I can not boot in my Ubuntu 14. In the recovery mode I got a root prompt with 'read-only' file system. I can not create nor modify any file or directory.

Can someone help me please?

Thank you very much!

---

### Post by Bashing-om on 2015-10-28
chuchi; Hi !

On my 14.04.3 install:
```

sysop@1404mini:~$ ls -al /lib/x86_64-linux-gnu/libudev.so.1
lrwxrwxrwx 1 root root 16 Oct  7 00:58 /lib/x86_64-linux-gnu/libudev.so.1 -> libudev.so.1.3.5

sysop@1404mini:~$ ls -al /lib/x86_64-linux-gnu/libudev.so.1.3.5
-rw-r--r-- 1 root root 67600 Oct  7 00:58 /lib/x86_64-linux-gnu/libudev.so.1.3.5
sysop@1404mini:~$

```

You may verify on your system these files exists, and redo the symlink in accordance.
From the recovery  console, terminal command:
```

 mount -o remount,rw / ##(Note there is no space after the comma.)##

```
to remount '/' with read/write access.
[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by chuchi on 2015-10-28
Hi Bashing-om

You saved my life!!

Thank you very much!!

---

### Post by Bashing-om on 2015-10-28
chuchi; Hey !
:)

If this is all it takes to get ya up and running ... 
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we have more fun
[INDENT][INDENT][INDENT]another time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chuchi on 2015-10-28
Done Bashing-om! 

Thanks a lot! you are a great Linux expert!

---

### Post by Bashing-om on 2015-10-28
chuchi; Awwhhh ...

shucks
> 
Thanks a lot! you are a great Linux expert!


I have learned from the best. - This forum is great -

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

