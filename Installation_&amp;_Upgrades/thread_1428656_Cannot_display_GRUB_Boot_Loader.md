---
title: "Cannot display GRUB Boot Loader"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by adeklipse on 2010-03-13
Alright, a few days ago, I recently installed Windows XP. I knew that the GRUB Boot Loader would not display itself after installation, and I know that to get it back, I would have to type in the terminal.
So I ran the LiveCD and typed

```
$ sudo grub
```and expected the terminal to enter the grub configuration.
But it DIDN'T! It said that there is no such command as "grub".

Please note that, before installing WinXP, I did do some partition changes with GParted. I believe that this is why the terminal cannot find the "grub" command. Also note that all my partitions are ext3, instead of ext4, so it could be identified be PartitionMagic.

I (used to) have 6 partitions: Windows, Data, /, swap, /home and /boot. The changes I made with GParted were changing the size and moving swap, / and /boot. However, in the LiveCD (after installing WinXP), it only shows 4: Windows, Data, "20 GB Extended" and "535 MB Filesystem". I suspect that "20GB Extended" is the Linux partition and the "535MB Filesystem" to be the /boot.
In GParted (in the LiveCD), it says there are absolutely NO partitions in my harddisk. My only response is, of course, WTF?

Please help me, I'm getting desperate... :(

---

### Post by mikewhatever on 2010-03-13
What version of Ubuntu are you running? Can you post the output of <sudo fdisk -l>.

---

