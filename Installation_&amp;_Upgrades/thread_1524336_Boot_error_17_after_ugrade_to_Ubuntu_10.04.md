---
title: "Boot error 17 after ugrade to Ubuntu 10.04"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by RGUFM on 2010-07-05
Hello everyone!

I haven´t posted anything here before even though I´ve used this forum successfully to find answers to several questions. But this time, I wasn´t able to find a solution...

My actual problem:

Yesterday, I did an online upgrade to 10.04, but got an error message  before the "cleaning up" phase, stating that there was an error and the computer might not be able to start, which proved to be true. When trying to boot, I always receive an error 17.

My system has also a Win7 partition as well as a common data partition, which can be used by both Ubuntu and Windows. The windows system still starts up normally.

I ran the boot info script and attached the results....

Any ideas suggestions on how to recover my system...?? Thanks in advance!


- Matt

---

### Post by hsoulen on 2010-07-05
Hello!

Sorry you ran into this issue.

I have had a look through your results.txt file and I just have a couple of quick questions:


[LIST=1]
[*]From what version of Linux did you upgrade? I ask this because it seems you have a number of older kernels available and it seems you are running ext2
[*]Can you boot to any kernel on the list or do all give the same error?
[*]I am assuming /dev/sda4 is your shared data partition?
[/LIST]
My first bit of advice is to get the Live CD, boot it up and run GParted, make sure you pick the correct disk from "GParted -> Devices" then post a quick screenshot of what your partition table looks like.

From your attachment I can't see anything "glaring" wrong (maybe someone else will spot something I am missing).

Cheers,

Hank

---

### Post by oldfred on 2010-07-05
Did you add the windows partition. You grub menu says this for booting Ubuntu 10.04:
root        (hd0,0)

With old grub hd0,0 is sda1 which is windows not Ubuntu.

At the grub menu can you press e and edit the entry to be hd0,1 for sda2 and see it it boots.
Then run sudo update-grub

---

### Post by RGUFM on 2010-07-05
Hank,

thanks for your comments. Some answers to the questions you mentioned:

1. I upgraded from 9.10, which has been upgraded from 9.04 (or even 8.10, not sure anymore). Anyway I still have the older version of grub which came with the earlier release.
2. I get exactly  the same error with every other boot option except win7.
3. Yes, /dev/sda4 is my data partition, which is also used by win7

Attached some screenshots from Gparted with separate info on each partition.

Oldfred,

I didn´t make any changes to Grub, it worked perfectly in 9.10. and win7. Win7 still works, but every boot option for Ubuntu will give me the same error.  I´ll try to make the change you mentioned and see what happens.

---

### Post by RGUFM on 2010-07-05
Hello again,

changing        (hd0,0) to        (hd0,1) did the trick!  It didn't boot all the way at first and it even returned the menu which I had just changed back to        (hd0,0) by itself, so I got the same error at first, but after changing it again I'm up and running and everything seems to work just fine...

Thanks to all of you for your great help, this really saved my day!! 

Cheers!
- Matt

:popcorn:

---

