---
title: "Error message when Ubuntu boots"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by Nepolean on 2011-09-02
Hello Everyone,

This is my first post here and I am totally new to Ubuntu.
I just installed Ubuntu day before yesterday alongside Windows and I see some error messages every time Ubuntu boots. I already searched the forum and found an answer to my problem, but I still have a question. The error message that I receive is 

' missing modules (cat/proc/modules ; is /dev)
/dev/disk/by-uuid/829070B79070B371 does not exist. Dropping to a shell '

This problem, it seems, is caused if a 32 bit version of Ubuntu is installed in a 64 bit machine. But in my case I guess I have installed a 64 bit OS in a 32 bit machine. Is it possible for this to happen? I have installed the 11.04 version and as a result of this problem  the Unity desktop has been replaced by the Gnome desktop. Please let me know your thoughts.

Thanks,
Nepolean

---

### Post by 2F4U on 2011-09-02
You can install the 32 bit version without any problem in a 64 bit machine. You may, however, not see all the RAM. My understanding is that it is impossible to install 64 bit version of Ubuntu on a 32 bit machine. You would not even be able to boot.

---

### Post by wojox on 2011-09-02
> **Nepolean said:**
> But in my case I guess I have installed a 64 bit OS in a 32 bit machine.

Not possible to install a 64 bit on a 32 bit machine. Double check. :P

---

### Post by Nepolean on 2011-09-03
> **wojox said:**
> Not possible to install a 64 bit on a 32 bit machine. Double check. :P

You're right. For a long time I thought that my CPU was 32 bit, I just checked and found that I have a 64 bit processor. :P I've been installing 32 bit softwares all the time!

But still, I don't know what's causing my problem.

Thanks, wojox and 2F4U, for responding to my query.:P

---

### Post by dino99 on 2011-09-03
from the first post:  /dev/disk/by-uuid/829070B79070B371 does not exist.

so you need to update with the good uuid. From a terminal run:

sudo blkid

to get your (good) uuid(s), then :

sudo gedit /etc/default/grub

and change the wrong uuid by the good one

sudo gedit /etc/fstab

and change it there too (if it exist (the wrong one)

then: sudo update-grub

---

