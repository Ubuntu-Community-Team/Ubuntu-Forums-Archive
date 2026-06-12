---
title: "Instul Ubuntu 10.10 On Single Drive With Vista"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by kevsim on 2011-02-28
I wish to install Ubuntu 10.10 on the same drive as Windows Vista, Drive "C".
During the installation process it gives 4 choices for installation.
If I choose the last choice No4, I can choose a partition, does this only format that partition or the total disk.
Can I make a seperate partition for Ubuntu?
I tried this using the "D" partition made from Windows, but receive the error "No root file system installed".

Is there a good explanation of all the 4 choices?

I would like to get this right the first time, as some other friends also want to start using Ubuntu.
I have done this on multi drives but that was a little different. 

I would appreciate some more advise.
kevsim

---

### Post by Dutch70 on 2011-02-28
This should help...

 [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

with pictures... :P
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

### Post by Mark Phelps on 2011-02-28
Do NOT allow the Ubuntu installer to shrink your Vista install to make room.  Doing so is asking for trouble as that sometimes corrupts the Vista install, rendering it unbootable.

A much better solution is to use the Vista Disk Management utility to shrink the Vista partition to make room for Ubuntu.  But, leave the unallocated space unformatted.

When you go to install Ubuntu, be VERY CAREFUL about formatting that partition.  If you make a mistake, you will erase your entire Vista install.

---

### Post by kevsim on 2011-03-01
I thank you for the replies.

When installing I stated 4 choices but a second look shows only 3 choices.

I would appreciate a detailed explanation on the 3rd choice as when I try it I receive "No root file system installed".
I added an extra partition but the same result, except I receive a message about no Swap file and can cause problem installing.

What should I be selecting when installing this way?

kevsim

---

