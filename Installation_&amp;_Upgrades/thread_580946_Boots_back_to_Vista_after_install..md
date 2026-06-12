---
title: "Boots back to Vista after install."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by PixelDJ on 2007-10-19
Hello, I just finished installing Ubuntu 7.10 and it said it finished successfully. I'm trying to dual boot Vista and Ubuntu. After the installation it prompted me to take out my CD and hit ENTER, so I did. Now my PC restarts and boots back into Vista like before...no Ubuntu. I'm kind of a noob when it comes to boot partitions and stuff, so if anyone can help me I would appreciate it.

Thanks
-Rob

---

### Post by Druke on 2007-10-19
what kind of pc is this, also do you have multiple HD's

---

### Post by PixelDJ on 2007-10-19
AMD64 3500+
NVIDIA 8800GTX
2GB RAM

3 HDDs
1: 320GB SATA
-Vista partition (80GB)
-Linux partition with Ubuntu (ext3) (18GB)
-Linux swap partition (2GB)
-Data partition (NTFS) (198GB)
2: 320GB SATA
-Data partition (NTFS) (320GB)
3: 500GB SATA
-Data partition (NTFS) (500GB)

Used amd64 version of Ubuntu 7.10

---

### Post by Druke on 2007-10-19
very strange, I would think it'd work perfectly... its not finding GRUB clearly, so the MBR was not overwritten. Seeing vista is your first partition that may have prevented the writing but I am not sure.

---

### Post by PixelDJ on 2007-10-19
Hmm...I guess I can try using EasyBCD and see if that works.

---

### Post by logos34 on 2007-10-19
I wonder if Grub installed on another drive...try booting from the other disks.  On the other hand it may not have installed at all for some reason

---

### Post by PixelDJ on 2007-10-19
Uh, yeah it installed GRUB onto my 500GB data drive for some odd reason. Is there an easy way for me to install it onto my main drive with Vista and Gutsy instead?

---

### Post by logos34 on 2007-10-19
You can try[ reinstalling grub from livecd]("http://ubuntuforums.org/showthread.php?t=224351").  Install to (hd0), and hopefully it will go on the mbr of your vista/ubuntu disk.

---

### Post by PixelDJ on 2007-10-19
Yeah, I'll try that. Now I'm having the blank screen issue when booting into Ubuntu from GRUB (on my 500GB drive) so I'll have to resolve that too.

---

### Post by PixelDJ on 2007-10-19
Okay, so it turns out that my 1st SATA master drive really isn't hd0. My 500GB (which my BIOS says is my 3rd SATA drive) is hd0.

I typed:
```
find /boot/grub/stage1
```
and got:
```
(hd1,5)
```
So apparantly my linux partition is on hd1, right? That's the same drive as Vista, so I figured I'd try this:
```
root (hd1,5)
setup (hd1)
```

Now when I reboot, GRUB shows up, but now when I try to boot Ubuntu from my main HDD it says "Partition not found" and when I try to boot Vista it says it's loading but just stays there, so I have to reboot and load the 500GB drive so that I can choose Vista.

I guess I did it wrong, heh.

---

### Post by logos34 on 2007-10-19
> **PixelDJ said:**
> Okay, so it turns out that my 1st SATA master drive really isn't hd0. My 500GB (which my BIOS says is my 3rd SATA drive) is hd0.

Strange.  Maybe grub is reading the drives according to their order on the sata channels (sata0, sata1, sata2, ...).  If your 500GB drive were IDE it would make sense (grub often detects pata/ide ahead of sata).

> ...So apparantly my linux partition is on hd1, right? 

yes, or so it would appear.
> 
That's the same drive as Vista, so I figured I'd try this:

```
root (hd1,5)
setup (hd1)
```

Now when I reboot, GRUB shows up, but now when I try to boot Ubuntu from my main HDD it says "Partition not found" and when I try to boot Vista it says it's loading but just stays there, so I have to reboot and load the 500GB drive so that I can choose Vista.

I guess I did it wrong, heh.

Good deduction.  But even though '(hd1)' worked and grub installed to the mbr, the minute you change it in the Bios to be the first boot drive it becomes (hd0).  So on the grub menu screen highlight the Gutsy kernel, then hit 'e' to edit, hit 'e' again on 'root' line and change to (hd0,5).  Press 'enter' to save and 'b' to boot.  If it works go to your menu.lst and edit it accordingly:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup**

**gksudo gedit /boot/grub/menu.lst**

*Change root (and 'groot') lines to (hd**[COLOR="Red"]0[/COLOR]**,5),  Also change vista entry to (hd**[COLOR="Red"]0[/COLOR]**,0) and take out any 'map' lines

---

### Post by PixelDJ on 2007-10-19
> **logos34 said:**
> Good deduction.  But even though '(hd1)' worked and grub installed to the mbr, the minute you change it in the Bios to be the first boot drive it becomes (hd0).

Ah, good point. I didn't even think about that. Yeah, when I change it to hd0,5 it works, but I'm still trying to work out my blank screen problem so I can't edit the menu.lst yet.

Thanks!

---

### Post by Can+~ on 2007-10-19
I had a similar issue (with Feisty), I used Gparted with the live CD to know which hard disk/partition I needed.

---

