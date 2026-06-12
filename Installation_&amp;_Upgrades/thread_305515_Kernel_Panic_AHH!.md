---
title: "Kernel Panic AHH!"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by Darrious on 2006-11-23
I'm having a problem with my kernel. I've had this happen to me before in dapper but there was at least a second choice I had in the grub menu and I was able to at least boot into ubuntu.

Now I installed Edgy and it says kernel panic, and there is no second choice on the list.  I reinstalled it a second time, but the same thing is still happening. I've never had this much trouble in dapper.

PLEASE HELP!!!](*,)

---

### Post by Darrious on 2006-11-29
This is really becoming a problem

---

### Post by diepruis on 2006-11-30
What is the complete error message?

---

### Post by Darrious on 2006-11-30
The error message is this when I boot.

```
Starting Up ...
             [17179573.840000] crc error
             [17179573.840000] Kernel Panic - not syncing: VFS: Unable   to  mount root fs on un-known-block(0,0)
             [17179573.840000] 
```

---

### Post by zgornel on 2006-11-30
Try appending *root=/dev/<root_partition>* or *root=UUID=<root_uuid>* to the kernel parameter list at startup.

---

### Post by Darrious on 2006-11-30
Sorry, but what are you talking about:confused::confused::confused:

---

### Post by zgornel on 2006-11-30
Check out section 7.4.1.4 : [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html)

---

### Post by Darrious on 2006-11-30
Two things.

1. How exactly does this help me.
2. What do I need to do. Is there something I need to type in the terminal?

---

### Post by diepruis on 2006-12-01
> **Darrious said:**
> Two things.

1. How exactly does this help me.

The kernel cannot mount the root filesystem. Those commands might help it, espcially if the error results from the kernel not being able to find the partition.

> **Darrious said:**
> 
2. What do I need to do. Is there something I need to type in the terminal?

Go read the part of the link that zgornel gave. That explains everything you need to know. If you still don't understand, the rest of that file explains things a *lot* more clearly than I could.

---

### Post by anubhavrocks on 2006-12-01
i guess you have broken initrd

---

### Post by Darrious on 2006-12-02
I have just decided reinstall edgy and what do you know.

I finally works. Anyway, I read what the link pointed to and I think I might have figured out my problem.

---

### Post by diepruis on 2006-12-02
As long as it works, eh? Happy ubunting!

---

### Post by Darrious on 2006-12-05
Well Now it doesn't work.

I just got another KERNEL PANIC!!!

This is starting to get aggravating.

I just reinstalled Ubuntu 4 days ago, and I'm getting another kernel panic.

It says the exact same thing.

Please Help!!!.

---

### Post by diepruis on 2006-12-06
Tried [zgornel's suggestion](http://ubuntuforums.org/showpost.php?p=1828600&postcount=5)?

---

### Post by Darrious on 2006-12-06
Actually...

I don't know how to do that. Is he wanting me to add *root=/dev/<root_partition>* or *root=UUID=<root_uuid> *
to a certain text file or folder. And if so which one.

---

### Post by anubhavrocks on 2006-12-07
why dont you install another kernel,

 sudo apt-get install linux-image-2.6.15-23-386 

assuming you have x86 based machine,use this kernel alongwith the 2.6.17

---

### Post by Darrious on 2006-12-07
ARRR!

I don't get the kernel message and I boot into my computer just fine.

I'm very glad, but I don't know what I did. There was this one post where I typed in about 3 command lines and the second command line I typed in... Didn't work!

This has been happening frequently. The Kernel being messed up I mean. Then somehow it is fixed and I don't know how. I've tried several different methods in order to fix my Kernel. Then the method does not work. I post about, try to find an answer, then I reboot really quick just to make sure it isn't working. Then, what do ya know. It works.

Oh well. I'm just glad I got ubuntu back :smile:

P.S. But that doesn't mean that I won't be posting here again for another kernel problem:mrgreen:

---

### Post by diepruis on 2006-12-08
I would suggest that you're not fixing the problem at all. It's just that the problem seems to show up at random intervals.

---

### Post by Darrious on 2006-12-09
That pretty much sums it up. I really have nothing to do with fixing the problem.

---

### Post by Darrious on 2006-12-11
Okay here we go again. The exact same thing just happened. I got another kernel panic and I'm running off of the live cd again.:rolleyes:

---

