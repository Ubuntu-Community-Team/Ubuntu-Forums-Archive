---
title: "Problem after installing Ubuntu on usb drive"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by bvross on 2010-07-15
I'm using Ubuntu 8.04 on my laptop and, before installing 10.04 on the internal drive (/dev/sda), I wanted to keep 8.04 on an external usb drive (/dev/sdb).
So I installed 8.04 from the live cd on /dev/sdb and after that everything was OK, except that the pc seems to take /dev/sdb as the primary drive.
When booting, the grub menu on /dev/sdb is used. From that, I can select the system on /dev/sda (Ubuntu as well as Vista).
But if the external drive is not connected, grub gives an error (21) and stop.
How could I make the system use the grub directory on /dev/sda, so that it can be started on the internal drive?

Thanks for your help.

---

### Post by blueysak on 2010-07-15
> **bvross said:**
> I'm using Ubuntu 8.04 on my laptop and, before installing 10.04 on the internal drive (/dev/sda), I wanted to keep 8.04 on an external usb drive (/dev/sdb).
So I installed 8.04 from the live cd on /dev/sdb and after that everything was OK, except that the pc seems to take /dev/sdb as the primary drive.
When booting, the grub menu on /dev/sdb is used. From that, I can select the system on /dev/sda (Ubuntu as well as Vista).
But if the external drive is not connected, grub gives an error (21) and stop.
How could I make the system use the grub directory on /dev/sda, so that it can be started on the internal drive?

Thanks for your help.
You will have to install the grub on the external hard drive, I am pretty sure but not positive. (I am reeally new so I would search install grub on usb)

---

### Post by Zimmer on 2010-07-15
This all depends on whether the external drive was plugged in when you installed 10.04 and whether or not you used the Advanced button to specify where to put GRUB2 when you installed 10.04..
Can you remember ? Probably not...

Suggestion:
Read about how to install GRUB2 and how to update it...
leave the external drive unplugged , use a SuperGrub disk (or a live 10.04 CD might do) to install GRUB on the laptop MBR. 

This should have the effect of GRUB (that may already be installed in the MBR of your laptop drive) re-organising its menus without the external drive.

What ought to happen is that if the External drive is plugged in before boot and GRUB2 is already there and the BIOS is set to boot from the External 1st...then the GRUB menu from the external drive will take command.

If the external is missing on boot, then the GRUB on the internal MBR will do its stuff.

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by ajgreeny on 2010-07-15
> **blueysak said:**
> You will have to install the grub on the external hard drive, I am pretty sure but not positive. (I am reeally new so I would search install grub on usb)
Yes, that is correct, but you will also need to restore the windows bootloader to the MBR.  You can do this with your Windows CD if you have one otherwise you can get the utility you need from neosmart here
[http://neosmart.net/](http://neosmart.net/)

With the external disk attached run ```
sudo grub-install /dev/sdb
``` in terminal which will put grub on the external.  However, until you have restored the windows bootloader you will need to keep the usb disk attached in order to boot windows.

Having done both these things just set your machine to boot first from the usb disk, and second, from the internal disk.

Job done!

---

### Post by bvross on 2010-07-15
I'm not sure I expressed myself well.
I did not yet install 8.10. I still intend to do so, but I would like to correct the boot problem first.
Also, the problem is not installing grub on the external drive. Grub _is_ on that drive and works well. But I want to have grub started on the _internal_ drive (as it was before the last installation of 8.04 on the external drive). The grub directory is still present on the internal drive, but when the computer boots, he starts grub on the external drive, and I do not want that, because I want to boot also when the external drive is not plugged.

Thanks again.

---

### Post by C.S.Cameron on 2010-07-15
You can fix the grub legacy on your internal drive using these instructions:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Once done your Windows should be OK also.

However since you are planning on installing 10.04 on your internal drive why not do that and it should fix everything.

I don't think you need to fix your windows MBR since there is grub on the disk.

---

### Post by bvross on 2010-07-16
Thank you for the link. It worked fine. :P

---

