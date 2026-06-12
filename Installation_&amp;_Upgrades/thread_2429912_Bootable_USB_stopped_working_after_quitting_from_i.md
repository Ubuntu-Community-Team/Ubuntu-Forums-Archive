---
title: "Bootable USB stopped working after quitting from install"
date: 2019-10-24
forum: Installation &amp; Upgrades
---

### Post by beh333 on 2019-10-24
Hi, I am new to Ubuntu. I am stuck in my attempt to make a dual boot machine with my ThinkPad X1 Yoga with Windows 10 Pro. Yesterday I made a bootable USB stick with Ubuntu Desktop 18.04.3 and it worked (running Ubuntu without installing it). So today I backed up my hard drive and tried installing Ubuntu from the USB. It was working but I decided to quit the install after a couple concerning things: (1) I didn't understand a warning about "the following disks have mounted partitions /dev/sda/" and (2) in the next screen after that warning, I felt like I needed to stop and think more about partitions. So I quit the install and researched partitions. 

My subsequent install attempts have been problematic since I quit that otherwise successful first install. I have had problems with USB booting and/or Ubuntu not recognizing Windows. If I use my standard BIOS settings, then the USB fails immediately on booting with a "something is seriously wrong" error related to missing EFI. (This is my first exposure to secure boot FYI.) If I edit my BIOS settings to boot with legacy or CSM, then the USB does boot. However, the install says that it detects no operating system. That sounds bad -- I don't want to install without Ubuntu recognizing Windows, especially because this morning it did recognize windows.

I would really appreciate help. I have tried recreating the USB, with no effect. I have reset BIOS and that does not help. I tried making a bootable gparted USB stick and that fails with the same EFI issue as my Ubuntu USB stick.

One possible clue, a thing that puzzles me, is that the very first time I used the Ubuntu USB stick, it asked me if I wanted to provide a secure boot password. I entered it (twice) and then I have never seen anything related to boot passwords again. I would think that creating a new USB stick would bring me back to that same question, but I only saw that question the very first time I made a USB stick.

Thank you for your advice!

---

### Post by yancek on 2019-10-24
The link below is the Ubuntu documentation on dual booting with windows UEFI.  Have you read it?  If not, do so and come back if you have questions.  THere are several steps necessary before you begin and those are listed at the site.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Skaperen on 2019-10-24
did you edit any BIOS settings, yet?  i'm wondering if it changed anything using the passwords you entered.  does Windows still boot up as usual when the USB stick is not in the ThinkPad?  do you have backups of Windows and/or your data?

---

### Post by beh333 on 2019-10-25
Thank you @yancek and @skaperen for your replies. The UEFI documentation is good background info.

I found a documented bug that is exactly what I am experiencing: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171). It has been fixed in 19.04 and so I will try making a new live USB with that.

The nature of the bug is (1) start install but quit after checking 3rd party drivers and providing boot password, (2) live USB never works again.

After I try installing 19.04 I will report back.

---

### Post by beh333 on 2019-10-25
Success! I re-created my live USB with Ubuntu Desktop 19.10 instead of the long-term-stable 18. The new USB worked perfectly. For what it's worth, I had to disconnect my external hard drive before the "install alongside windows" option would choose my internal SSD instead of insisting that Ubuntu boot from the external drive. That was simple and I am running Ubuntu on my newly configured dual boot machine. Ready to go!

---

