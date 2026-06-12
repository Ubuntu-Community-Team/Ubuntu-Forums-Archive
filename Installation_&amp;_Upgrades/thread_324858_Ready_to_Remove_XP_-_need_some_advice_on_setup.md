---
title: "Ready to Remove XP - need some advice on setup"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by shane2peru on 2006-12-24
Ok, here is the deal.  I have been successfully dual booting for about a year and a half, and sometimes I was triple booting.  I'm very content with Ubuntu, and wine has gotten 10x better and runs the two programs I can't live without (ACT6.0, and E-Sword).  And runs them very well now I might add.  I have a 40GB hdd, here is the layout:
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2493    20024991    7  HPFS/NTFS
/dev/hda2            2494        3138     5180962+  83  Linux
/dev/hda3            3139        3787     5213092+  83  Linux
/dev/hda4            3788        4864     8651002+   5  Extended
/dev/hda5            4785        4864      642568+  82  Linux swap / Solaris
/dev/hda6            3788        4784     8008339+   b  W95 FAT32

```

hda1 20GB for Windows XP, that I haven't booted into in about 2 months now.  
hda2 5GB for Ubuntu / filesystem
hda3 5GB for my /home
hda5 640mb for swap
hda6 8GB for my data for both file systems.  

I do have external hdd that I can back everything up to, and do run regular backups with the tar command.  What I need to know, is 

1.  What is the best method to partition this drive up for Strictly Ubuntu.  I'm thinking that /home should be a separate partition, but I'm not 100% sold on this because I have had problems with upgrades ect, where I have needed to wipe my /home and start from scratch which makes it almost pointless to have a separate /home partition.  Pros?  Cons?

2.  What is the best method to keep all my data and just transfer it to my new setup?

3.  Should I save a little room for tinkering with other distros?  (I do like to see them, and have tried a variety from Gentoo, Slackware, Debian, Mandriva, FC, etc)  I have never been as impressed as I have with Ubuntu.  I would not plan on mixing my /home with my Ubuntu distro, I have messed things up that way in the past.

4.  Is there anything particular I should know about erasing my XP partition and going strictly Ubuntu?  

Thanks for the help!!!

Shane

---

### Post by meng on 2006-12-24
1. I see no drawbacks to having a separate /home partition. Bully for you that you never had a problem with upgrades before, but don't ride your luck off into the sunset now!
2. There are many ways to skin a cat here. What I'd be tempted to do in your situation:
a) Run Gparted LiveCD (latest version), delete Windows partiton, move/resize other partitions, then reinstall Ubuntu over the partition for / (currently hda2)
3. If you have spare space, keep some of your disk unallocated for whatever purpose tickles your fancy in future.
4. Just in case, it's a good idea to back up your data before attempting anything like this (especially with repartitioning), no matter how safe you think it may be. Otherwise nothing you haven't come across in the last 18 months I would imagine.

---

### Post by shane2peru on 2006-12-24
> **meng said:**
> 1. I see no drawbacks to having a separate /home partition. Bully for you that you never had a problem with upgrades before, but don't ride your luck off into the sunset now!

No, I think you misread my first post, > 1. What is the best method to partition this drive up for Strictly Ubuntu. I'm thinking that /home should be a separate partition, but I'm not 100% sold on this because **I have had problems with upgrades ect, where I have needed to wipe my /home and start from scratch** which makes it almost pointless to have a separate /home partition. Pros? Cons?

Any I wish I had that kind of luck!  :-D   Anyway, I appreciate the reply.  More advice is welcomed, like best backup method, best transfer method, I'd like not to have to setup my Ubuntu again. (I usually use the tar method from the HOWTO's of this forum.) Thanks!

Shane

---

### Post by meng on 2006-12-24
Whoops I badly misread your post!!!
IMHO, the safest way to preserve your data is by having a separate /home AND doing a reinstall with the new version (i.e. an overwrite rather than an upgrade) but you must be really careful with the manual partitioning step, and make sure 1) you keep existing data on your /home partition and 2) correctly identify the mountpoint (although this is less critical, you can always change the fstab later).

---

### Post by shane2peru on 2006-12-26
Well, if anyone else has any ideas, or wants to give any input, I certainly welcome the ideas!  Thanks.

Shane

---

### Post by shane2peru on 2006-12-26
I'm just thinking out loud here.  What if I go ahead and partition out about 8GB of my Window Partition as ext3, and make that my new root partition.  I could just copy everything from my current root over (probably with the tar and then untar it unless you know a simpler way ;) ).  I could then modify my menu.lst and add it as a separate boot option.  I then could boot into it and make sure that all is well there.  Is 8 GB big enough for the / of Ubuntu?  I'm currently running it in only 5, so I think 8 would be fine, It would give me a little room to grow if needed.

Next I would copy all my /home partition data to a bigger partition change all mount points reboot to make sure my new home was mounted correctly and running.  That would leave my two partitions I'm currently running on untouched until these operations were complete and running.  

Next I would have to re-install grub - not too difficult so that it would look for the grub menu in the new location hda1, and not hda3 where it currently is located.  

Then delete my current two partitions and mold them into one partition for misc usage.  Attached is a screen shot of Gparted for people like me that like to see how there hard drive is divided up.  Does this sound like a workable plan?  

Shane

---

### Post by shane2peru on 2006-12-27
Ok, step one and two have gone very well.  I'm running off my new root partition and even booted off of the grub menu that was on this partitions root, which means I successfully reinstalled grub!  Working on transferring /home.

Shane

---

### Post by shane2peru on 2006-12-27
ok, got my home all switched - WOW THAT WAS EASY!!!  I don't think I could have done that in Windows.  :-D   Nice to have all the space.  Just thought I would keep anyone informed that was reading this thread.

Shane

---

