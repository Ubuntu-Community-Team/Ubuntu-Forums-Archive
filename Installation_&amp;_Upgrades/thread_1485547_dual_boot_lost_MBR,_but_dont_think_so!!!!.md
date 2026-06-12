---
title: "dual boot lost MBR, but dont think so!!!!"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Dn4mycrownj on 2010-05-17
I have an external 80GB hdd that is hooked to usb. I partitioned this hard drive to 50GB for my music. Then I partitioned 20GB for ubuntu 9.10. I did the partition with vista. The other hard drive is a 750GB internal. 1 factory partition and the rest is drive C: .  
If i run sudo gedit /boot/grub/menu.lst    The page that is returned is blank.   
When i run sudo fdisk -lu    it returns this 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6669724e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20482874    10241406   27  Unknown
/dev/sda2   *    20484096  1465145343   722330624    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe93aa3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   115336382    57668160    7  HPFS/NTFS
/dev/sdb2       115346700   156296384    20474842+   5  Extended
/dev/sdb5       115346763   154497104    19575171   83  Linux
/dev/sdb6       154497168   156296384      899608+  82  Linux swap / Solaris
bighead@bighead:~$ 

The Vista is 64bit and the Ubuntu is 32 bit. Could this be the problem?
My vista is still there. On the 750GB. I was real cautions on what i did. I just didnt expect this.  My question is how can i get grub to load it from a different hard drive.  And if not what can i do to get my vista hard drive to load. The first would be better but the second may be a need for work. 

Oh yeah, I am on the linux on the external HDD. It loads just fine. If i Unplug the external HDD it does not load at all. 

If you guys need any thing else just ask. I do not know what else to do.

---

### Post by bcbc on 2010-05-17
It sounds like you installed grub to the MBR of your internal drive. So, that would explain why nothing happens when you unplug the external (grub bootloader in MBR of internal looks on the external for the actual menu - which would be /boot/grub/grub.cfg on a fresh install of 9.10 by the way, no longer menu.lst).

You should still be able to boot vista with the external plugged in, regardless of 64 bit etc. If not, post the results of the [bootinfoscript]("bootinfoscript.sourceforge.net") and maybe we can figure out why vista isn't booting.

In any case, what you want to aim for is the windows (or equivalent bootloader) on the internal drive MBR, and grub on the external MBR. Then the default would be to boot into windows, unless you choose to boot from the external.

So to do this, boot ubuntu, and install grub to the MBR of the external /dev/sdb:
```
sudo grub-install /dev/sdb
```

Then install the windows (equivalent) bootloader to the MBR of /dev/sda)
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

After that windows will boot by default, unless you select to boot from the external.

---

### Post by lisati on 2010-05-17
Important note: Fresh installation of 9.10 and newer uses grub2, not grub - the configuration is different, hence menu.lst appears empty.

---

### Post by Dn4mycrownj on 2010-05-17
Your awesome ive looked ever where for an answer and you gave me one quick. 
That worked backed to vista.  Now Can I make it an option in the os selection screen provide by Win?   When i choose in the bios to boot usb first it does not pickup the os on the external. It goes straight into vista.  If you need what kinda bios i have, i can offer the information.

i am willing to edit something in 9.1 if i can figure out how to get back to it.

---

### Post by Dn4mycrownj on 2010-05-17
Lisati, bcbc  

on my laptop i have only upgraded from 8.04 i did not know it was different. On a clean install of 9.1 Thank you for the information.

---

### Post by Dn4mycrownj on 2010-05-17
I am willing to play with what ever to make this work. I can get back to vista now so when i figure out how to go back and forth it would be great to figure out how to load from the grub screen back to the internal hard drive and load win. If you people have ideas I got a little know how. 

I am willing to figure it out either way to be able to choose from a screen what i would like to boot for an os.

---

### Post by bcbc on 2010-05-17
I've seen posts about booting ubuntu from the vista menu using easybcd or grub4dos - but I have no experience doing this.

It's easier if you can get your computer to boot from the external - I just press F12 at boot up and select to boot from usb, but this obviously depends on your bios.

---

### Post by Dn4mycrownj on 2010-05-17
in my bios it recognizes the usb hard drive as a hard drive and not a usb device i can change the bios to load the other hard drive first. It would be alot eaiser if we could make it pickable from a list.

---

### Post by Dn4mycrownj on 2010-05-17
Got it figured out. There is a new program out

its called EasyBCD 2.0 Beta Builds,Build 93

That is what i used. This Supports grub2, grub and some other options, and is very very user friendly great GUI good for all beginners. It brings up the selection screen by its self on reboot. That program only runs in windows. This thing also recognizes the hard drive across usb.  This is the easy thing i have done in a long time on ubuntu. This program needs to be offered or told about to people. 

To get the beta program i had to sign up to a forum and verify email. Then it would let me download well worth it.  Only the beta is this easy the older version needs a hack to make work.

---

