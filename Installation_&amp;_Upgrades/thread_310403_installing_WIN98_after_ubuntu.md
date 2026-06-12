---
title: "installing WIN98 after ubuntu"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by crash0 on 2006-12-01
Hello.

**1. The "where":**

I have a fairly old IBM Thinkpad with Edgy. The disk (cca 28 GB) is divided up to 4 partitions:

[========== ext2 22 GB ======--------][ FAT32 ][==== ext2 4 GB ==---][ Swap]

(I haven't named the partitions with hda1/2/3 because the numbers got weird and mixed up during a lot of formatting-resizing-(re)moving).



**2. The "what":**

I would like to install Windows 98 SE on the FAT partition. The problem is that when I start the Win98 setup from the CD, it says that it has to format the whole drive. I tried to shift the FAT32 to the start of the HD, but the same thing happened there, so I figured that Win98 won't install if there are any partitions on the disk that it can't recognize (ext2).



**3. The "why":**

I WinXP installed normally a few weeks ago, but I wan't 98 because XP takes much more space (about 2.5 GB; W98 takes up less than 300 MB) and 98 is a bit faster (because my laptop is a bit slow and old).

I know it's better to install Windows before Linux, but I can't do this. Why? I have no place to back up ma data to and I don't wan't to go through the whole "basic-programs-apt-get-500-meg-download-can't-get-mplayer-and-video-card-and-printer-to-work" in Edgy.

I'm stuck because:
1.) I have no DVD-RW, internal nor external, to copy my files to
2.) I have no external HD to copy the files to, and even if I had one, my USB is 1.0 so it would take days to copy 20 GB back and forth

Why don't I try Wine or something, you ask? Very simple: I tried VMware, It worked but for some reason it would forget the settings each time I rebooted my comp, so I had to go through the setting-up-process each time. I tried Wine but it worked perfectly only for a 300kb program. It almost worked for 2 other programs, but there were some errors, crashes, and (ofcourse) everything was sooo slooow. Ergo, the mighty Dual Boot is all I have.



**4. The "how":**

So, I have a few questions about some tactics I came up with:

1.) Tactic #1

Is there a way to convert the ext2 partitions to fat32 without losing the files on them? Would Win98 then install without formatting the whole drive? Could Edgy be run on fat32 partitions?

2.) Tactic #2

I came up with a weird idea: I could shrink the ext2 partitions, grow the fat32 partition, then move the files from ext2 to fat32 and do this until the ext2 are empty and all I get would be one fat32 partition that would take up almost the whole drive. I would hide this partition, make a small 0.5 GB fat32 partition for Win98 and install Win98 onto this small partition. Then I would unhide the big fat32 partition and do the process backwards to get two new ext2 partitions for Ubuntu. Is this sane?

3.) Tactic #3

Is there a way to hide the ext2 partitions? Then I could install Win98 without it knowing that there are any other partitions except the fat32.

---

### Post by bernied on 2006-12-01
Tactic #3 
There is a way to chainload a CD through grub. Grub can also hide partitions. So you should be able to boot the CD into an environment where, as far as Windows can see, there is only that one FAT partition.

Here's a howto along similar lines (I didn't read it, so don't know if it does it the way I said):
[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

---

### Post by bernied on 2006-12-01
Here's a howto for enabling grub to chainload a CD:
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

---

### Post by kvonb on 2006-12-01
Can you boot from the 98 CD?  If so, when the simple menu comes up, don't select "Setup Windows 98", select "Start computer with CD ROM support" or whatever it is called, then do it manually:

The only problem is that if you run "fdisk" it will overwrite your boot sector which means that you will have to re-install grug which can be a pain, there is a good how-to on the forums somewhere, do a search and print it out!

If you can format the FAT32 partition through a 3rd party app such as "Partition Magic" or some other clone, it may keep your grub.

Anyway, once you have your formatted C: drive, just type "setup" and it will go through the normal install without formatting, just select the option to overwrite if it asks you.

---

### Post by milton1 on 2006-12-01
Don't do it. Even if you can install win98 without formatting the drive, win98 will screw your boot sector. For dual boot, install win98 first, then Ubuntu.

---

### Post by bernied on 2006-12-01
Boot sectors can be unscrewed. You can put a copy of your MBR onto a file and replace it later. See here:
[http://wiki.linuxquestions.org/wiki/Dd#Backing_up_your_Master_Boot_Record_.28MBR.29](http://wiki.linuxquestions.org/wiki/Dd#Backing_up_your_Master_Boot_Record_.28MBR.29).
It's all been done before...

---

### Post by milton1 on 2006-12-01
Good to know. :)

---

### Post by crash0 on 2006-12-02
Ok, so far half the work is done. Thanks to you all...

I managed to install it. I started Ms-dos by booting from the Cd then ran setup, after formatting the disk with a linux live rescue cd (instead of gparted). I installed Win98 on a 512mb fat32 partition.

However, it's full of errors. The first time I installed it, it asked me to put the cd because it couldn't find some dll files. It couldn't find them on the cd either, so I had to choose "skip". Now I have a Windows 98 Second Edition without half the system files. I'll try to fix something.

And concerning the grub: after the installation, I had to restore grub. I booted using a qtparted rescue cd, typed "grub", "root (hd0,2)", "setup (hd0" and everything's ok for now...

---

### Post by viciouslime on 2006-12-02
> **crash0 said:**
> However, it's full of errors. The first time I installed it, it asked me to put the cd because it couldn't find some dll files. It couldn't find them on the cd either, so I had to choose "skip". Now I have a Windows 98 Second Edition without half the system files. I'll try to fix something.

Lol, welcome to the world of windows ;) Good luck!

---

### Post by Sef on 2006-12-03
Read to [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub") from Ubuntu's documents.

---

