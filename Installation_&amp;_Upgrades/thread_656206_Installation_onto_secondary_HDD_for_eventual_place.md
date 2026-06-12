---
title: "Installation onto secondary HDD for eventual placement in another pc"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by finite9 on 2008-01-02
Here's an unusual installation question.

Most people want to install onto USB drive or USB stick or create a LiveCD on a USB stick etc etc.  Some even want to install without CDROM or install onto secondary HDD.  What I want is more unusual, and I cannot find any links and it wont be me doing this, it will be my dad who lives in another country so I cannot physically help him out....

He has a laptop whos CDROM drive died.  He cannot boot from USB as the motherboard does not support it.

He can however remove the disk and attach it to his other laptop using an ATA to USB converter cable.

Is it possible to boot the other working laptop using the LiveCD and install Ubuntu onto the secondary hard disk, and then write the grub stuff to the secondary hard drive instead of the MBR then put the disk in the old laptop and boot successfully?

Is it that simple?  Is there anything else I need to think of?

---

### Post by logos34 on 2008-01-02
If the target installation laptop has internet connection tell him to try [UNetbootin]("http://lubi.sourceforge.net/unetbootin.html") or the manual method described here:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

If it does not have internet he could still use the above guide but he'd have to transfer the .iso to the lappy via, say, usb stick.  Or maybe just network it to other laptop with crossover cat5 cable.

If he does the method you described, it might work--if he's lucky all he'll have to do is fix the graphics:

sudo dpkg-reconfigure xserver-xorg
(in terminal on desktop or at the prompt in recovery mode)

---

### Post by finite9 on 2008-01-03
I dont know if this will help me.  By the way I forgot to mention that not only does the laptop not have a cdrom but it has no floppy disk either.

The netboot method you linked to seems ok, but what if I want to format the entire HDD to ext3 during the installation?  Can I do this or do I have to keep the WinXP partition that I rnu netboot from and install Ubuntu into a separate partition on the same disk?

---

### Post by teetii on 2008-01-03
I confirm this. Just yesterday got new computer, rearranged some hard drives with my current ubuntu installation and other drive with very old xp/ubuntu setup.

Booted fine to KDE but resolution was wrong and could not be changed. 
**sudo dpkg-reconfigure xserver-xorg** solved that out, and I was good to go.

Both computers have nVidia graphics card and AMD processor, but 7 years time difference :)

---

### Post by logos34 on 2008-01-03
> **finite9 said:**
> I dont know if this will help me.  By the way I forgot to mention that not only does the laptop not have a cdrom but it has no floppy disk either.

The netboot method you linked to seems ok, but what if I want to format the entire HDD to ext3 during the installation?  Can I do this or do I have to keep the WinXP partition that I rnu netboot from and install Ubuntu into a separate partition on the same disk?

Floppy not needed.

You need to keep xp partition at least until installation is finished because that's where it running from.  Then you can format it from ubuntu using Gparted.  Turn it into an ext3 data partition or separate /home.

---

### Post by finite9 on 2008-01-06
ahh cack.  Things just went worse.  I did not really understand when my dad told me the situation that his windows install is broken!!  He cannot boot to Windows on his old laptop, because the cdrom drive was sort of working and he attempted to reinstall winxp but it only got a short way through the install before the cdrom drive failed.

So, he has a Toshiba laptop with no floppy and a seriously broken cdrom drive and he cannot boot from USB and the hard drive is basically empty, ie no working OS.

All the options I have looked at involve being able to boot from usb, cdrom or by booting to windows first then initiating some kind of install method.  He cannot do any of these.

The only thing he can do is connect the toshibas drive to another laptop using a USB to ATA converter cable.  He can see this drive OK in windows, but when he boots the LiveCD on the other workin laptop, then Ubuntu will not see the toshibas drive.  I do not know if this is due to a driver being needed for the adapter cable?  Anyway, 

```
sudo fdisk -l 
```

shows only his Dell laptop drive as sda and not the attached ATA drive over the USB cable.  Any ideas why?  I see this as my only option now, to boot the LiveCD on another laptop and install onto the Toshibas laptop then put it back in the toshiba and fix things if needed.

---

