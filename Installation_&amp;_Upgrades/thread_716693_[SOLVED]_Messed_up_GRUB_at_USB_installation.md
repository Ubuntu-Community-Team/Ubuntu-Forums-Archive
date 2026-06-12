---
title: "[SOLVED] Messed up GRUB at USB installation"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Captain Giraffe on 2008-03-06
I installed an ubuntu live CD on an USB memory stick, I expected to be able to configure the grub boot loader, but instead it didn't ask me anything at install time. So it replaced my current grub (grub dual boot SUSE/WinXP).
My problem is that the current setup requires my USB stick to be inserted to boot at all. My goal was to make a bootable usb (a la pendrive-linux.com)  and have my current setup intact. So I have two questions 
1- how do I revert to my previous grub configuration
2- how do I make my usb bootable with the current ubuntu installation.

Also as a secondary goal I'd like to encrypt the entire USB drive. Any ideas here?

Thanks in advance
/Captain G

---

### Post by louieb on 2008-03-06
To fix booting to the hard drive install of grub. You need to know which partition its install in and what grub calls it. 
In a terminal window (Applications>Accessories>Terminal) fire up GRUB
```
sudo grub
```
Now find your grub install
```
find /boot/grub/stage1
```
or if you made a separate /boot partition 
```
find /grub/stage1
```
Its going to return something like (hd@,#) maybe a couple of them one on the hard-drive on on the USB stick. You'll just have to figure out which is which.

Now you have the info to fix. Set the grub root to your hard drives install of grub. (use the real letter and number from the find command)
```
root (hd@,#)
```
Now change the mbr  to use grub on the hard-drive
```
setup (hd0)
```

To alter the hard drives grub menu to boot the linux install on the usb stick. Go to [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") it has all the  info you need to do that.

---

### Post by Captain Giraffe on 2008-03-06
Firstly thanks for the excellent information provided, it solved my problem and made me more educated in the process. 
I do have a followup; My intention is to not make the USB bootable from the default hd0 grub but rather as a bios chioce. I therefore need to make the USB bootable, I seem to recall that there are two types of MBRs one per hardware and one per partition?
So my followup question is this:
- How do I make my USB bootable, not from grub but from the BIOS selection?
I suspect grub will be involved in a secondary stage, and I'm fairly certain I can customize my USB grub to just boot my new fav OS.  On a side note Im writing this on my newly restored hd0 opensuse installation.

---

### Post by Captain Giraffe on 2008-03-06
Followup #2
I also would like to make all disk write caching as aggressive as possible while on the USB drive, how do I accomplish that? Is write caching disabled by default?
If I should perhaps post this in another forum, please met me know.  If msdn KB library only worked like this !lol!
/Captain

---

### Post by louieb on 2008-03-06
haven't set up a usb stick to boot. I believe they are like a hard-drive in  that they have an MBR at the start of the drive. and a boot sector at the start of each partition.  

To set it up so you can select the drive with BIOS to be the boot device.  
Its the same thing as you did with the hard-drive - only the root (hd#,#) and the setup (hd#) will change.

Don't know a thing about write caching.

---

