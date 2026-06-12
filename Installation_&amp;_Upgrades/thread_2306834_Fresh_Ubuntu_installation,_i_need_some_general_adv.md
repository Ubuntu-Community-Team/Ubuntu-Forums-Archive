---
title: "Fresh Ubuntu installation, i need some general advices"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by Nonoua on 2015-12-19
Hi all, this is my first post, im quite new to Ubuntu and i was wondering how to correctly manage my partitions and my hard drives to correctly make a fresh ubuntu installation.
I got two hard disk here (Samsung 600 Gb and Toshiba 1Tb) so my intention was to make something like that:

740 Gb /home on ext4
80 Gb of swap
640 Gb - Data partition on NTFS
and 150 gb for a win installation, Fat32

My question is, how would you manage that? 
Thanks for help and long live the ubuntu!

):P

---

### Post by v3.xx on 2015-12-19
80G of swap sounds like a lot.

Rule of thumb is swap equals your ram.

[https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F](https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F)

---

### Post by Nonoua on 2015-12-19
Im reading your link and thanks for your help. May i ask you a question? Is it completely useless to have such space for swap?
Can i also ask you how would you manage 1 Tb and 600 gb of space knowing my will to use some space for windows?
Thank you

---

### Post by ian-weisser on 2015-12-19
Personally, I avoid *all* the issues of dual-booting, and simply run other OSs in a Virtual Machine.
Linux, Mac, Windows all run quite good VMs.

It makes experimenting and changing your mind much easier and safer.

---

### Post by grahammechanical on 2015-12-19
You have not included a partition for Ubuntu.

Normally Ubuntu goes into a / mounted partition and inside the / directory there will be our /home folder. Which means that if we re-install we may loose everything in the /home folder. So, some of us put /home on its own partition. Well, you list 740GB for /home partition but nothing for Ubuntu. You need about 20 GB to 30 GB for / partition.

Regards.

---

### Post by v3.xx on 2015-12-19
> May i ask you a question? Is it completely useless to have such space for swap?

Funny you should ask.

[http://ubuntuforums.org/showthread.php?t=2306798&p=13409011](http://ubuntuforums.org/showthread.php?t=2306798&p=13409011)

---

### Post by Topsiho on 2015-12-20
You should first think of how much space you want to give to Ubuntu, and how much you think you need for Windows.
The space [COLOR="#008000"]you give to Ubuntu[/COLOR] can be divided into 3 separate partitions, that's what I use to do:
1. a partition for root, mountpoint is / (forward slash, symbol for the root partition). This will contain all system files. File system ext4. As you have plenty of room make it 20GiB. More than enough.
2. a partition for swap. Rule of thumb is 2*RAM. No use much thinking how large, 1*RAM would suffice, 2*RAM is certainly OK, and the amount is negligible.
3. the remaining space you allot to Ubuntu you should put into a third partition, /home. It will contain all files of the users of your computer. It will need a lot of space if they have large files, now, or some time in the future. It is the main thing that determines how much space you want to give to Ubuntu. File system is ext4.

I am afraid I am talking legacy when I mention that you can have only 4 primary partitions. One of which should be sacrificed for an extended partition, in which you can put an unlimited number of logical partitions. Someone may tell you more on this. I have only older computers :)

Topsiho

One extra note:

You should Windows (which I assume is installed first, it should be) let create the space in which you want to install Ubuntu. After that (and before installing Ubuntu) restart Windows to see if it recognises the new situation that it created itself. If you let Ubuntu (Gparted) create the new situation Windows is almost certain not to recognise the new situation, and fail to boot.

Topsiho

---

