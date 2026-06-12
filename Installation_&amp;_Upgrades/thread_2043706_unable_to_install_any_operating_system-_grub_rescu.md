---
title: "unable to install any operating system- grub rescue error"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by linespace on 2012-08-17
Hi,

I am unable to install/ recover any operating system on my notebook after running a Windows recovery that deleted Ubuntu. 
So in short, when the  laptop rebooted to complete the  Windows installation, I got a black screen  reading
 `error: no such partition
grub rescue> `

_What I tried to do to solve this and **did not work **was_:
- putting the Ubuntu liveCD in: no response whatsoever
- making and putting in the BootRepair Disk CD: same, no response 
- making and putting in the [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") CD: same, no response
- typing commands after `grub rescue` such as `setroot= (hd0,0)`: anything I typed would be an unknown command
- restoring the Windows XP bootloader: my recovery CD actually does not have the option restore or repair. 
[It`s a pair of Windows XPH CDs made especially for my old Asus   notebook- 2004- and the only options I get are: 1) MS-DOS with CD Rom   support; 2-4) Recover Windows XP to first partition/ entire HD/ entire   HD with 2 partitions]

- I also tried to run a Kasperski Rescue Disk, but also not response. 

Any  ideas? 

Because I had some problems with both of my operating systems, I need to  determine whether I have a virus or a hardware problem. So my aim is   to get to the point where I can run a Rescue Disk (Kasperski)  or- if I   can install an OS- run some virus scans (OTL, MBAM)

Many thanks in advance!

---

### Post by linespace on 2012-08-17
Hi,

I am unable to install/ recover any operating system on my notebook after running a Windows recovery that deleted Ubuntu. 
So in short, when the  laptop rebooted to complete the  Windows installation, I got a black screen  reading
 `error: no such partition
grub rescue> `

_What I tried to do to solve this and **did not work **was_:
- putting the Ubuntu liveCD in: no response whatsoever
- making and putting in the BootRepair Disk CD: same, no response 
- making and putting in the [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") CD: same, no response
- typing commands after `grub rescue` such as `setroot= (hd0,0)`: anything I typed would be an unknown command
- restoring the Windows XP bootloader: my recovery CD actually does not have the option restore or repair. 
[It`s a pair of Windows XPH CDs made especially for my old Asus   notebook- 2004- and the only options I get are: 1) MS-DOS with CD Rom   support; 2-4) Recover Windows XP to first partition/ entire HD/ entire   HD with 2 partitions]

- I also tried to run a Kasperski Rescue Disk, but also not response. 

Any  ideas? 

Because I had some problems with both of my operating systems, I need to  determine whether I have a virus or a hardware problem. So my aim is   to get to the point where I can run a Rescue Disk (Kasperski)  or- if I   can install an OS- run some virus scans (OTL, MBAM)

Many thanks in advance!

---

### Post by darkod on 2012-08-17
If you keep getting that message, doesn't sound like you are booting from the cd-rom. Go into BIOS and make sure the cd-rom is before the hdd in booting devices. You can also try to display a boot menu if the computer has that option during boot. It's usually with F12 or similar, depending on the computer. From the boot menu select to boot the cd-rom.

Once you sort that out, I am sure you will be able to install any OS that you want. The windows restore should have deleted grub from the MBR so it's very strange you are getting that message in the first place. But even if the restore needs to boot once to continue, you can put a generic mbr on the MBR using the ubuntu cd without installing ubuntu.

---

### Post by Codify on 2012-08-17
I agree it doesn't sound like you're booting from the CD. I've had a similar problem when trying to install Windows over a Linux install. I found that Windows didn't quite overwrite GRUB in the MBR. I had to boot up off the Windows XP disc and choose repair an installation. I ran the following commands from a command prompt: fixmbr and fixboot that did the trick and Windows booted afterwards. I've since used DBan to completely wipe the HDD of all traces of software. Fresh installs work very well then.

---

### Post by linespace on 2012-08-17
> **darkod said:**
> If you keep getting that message, doesn't sound like you are booting from the cd-rom. Go into BIOS and make sure the cd-rom is before the hdd in booting devices. You can also try to display a boot menu if the computer has that option during boot. It's usually with F12 or similar, depending on the computer. From the boot menu select to boot the cd-rom.

Once you sort that out, I am sure you will be able to install any OS that you want. The windows restore should have deleted grub from the MBR so it's very strange you are getting that message in the first place. But even if the restore needs to boot once to continue, you can put a generic mbr on the MBR using the ubuntu cd without installing ubuntu.
Hi Darko. Thanks for the response- I did make sure the laptop boots from the CD (by going into BIOS) when I first ran the Windows recovery...so if it is not anymore booting from the CD, the only idea I have is that it cannot read CDs properly- I did have some issues like that before. However it did read the Windows recovery CD- so I am back to a question mark. 
I had some problems during Windows recovery- so I guess that is why the grub is not deleted from the MBR as you say it should have been. Namely I was getting sth like `Boot Sector Write VIRUS: Continue (Y/N)?`...which could mean a virus in BIOS but maybe also the conflict of `rewriting` Windows on the disk (?)

---

### Post by darkod on 2012-08-17
> **linespace said:**
> Hi Darko. Thanks for the response- I did make sure the laptop boots from the CD (by going into BIOS) when I first ran the Windows recovery...so if it is not anymore booting from the CD, the only idea I have is that it cannot read CDs properly- I did have some issues like that before. However it did read the Windows recovery CD- so I am back to a question mark. 
I had some problems during Windows recovery- so I guess that is why the grub is not deleted from the MBR as you say it should have been. Namely I was getting sth like `Boot Sector Write VIRUS: Continue (Y/N)?`...which could mean a virus in BIOS but maybe also the conflict of `rewriting` Windows on the disk (?)

That sounds like some protection against writing to the MBR. If you said No that could explain leaving the bootloader alone.

There is really not much you can do until you are capable of booting with the cd. One thing you can try is making a bootable usb stick with ubuntu and booting with it if your computer supports usb boot.

---

### Post by claracc on 2012-08-17
Perhaps you can find better solutions in a microsoft win xp forum.

What I would do is:

Introducing the recovery win xp CD

Select option one: MS-DOS with CD support

enter the command fixmbr

---

### Post by linespace on 2012-08-17
> **darkod said:**
> That sounds like some protection against writing to the MBR. If you said No that could explain leaving the bootloader alone.

There is really not much you can do until you are capable of booting with the cd. One thing you can try is making a bootable usb stick with ubuntu and booting with it if your computer supports usb boot.
I finally managed to boot from a cd with the help of an external usb pluged dvd writer. So the problem now switches to the the other error that I mentioned: the boot sector write alert. 
Also Windows will stop the installation at some point because of the external dvd reader- says sth like CD01 not ready to read Y, but for some reason the cd from windows is readable with the incorporated dvd reader so I can work around that. 
Now, the last time I tried all this (tried it for at least 3 times- with the same result) I was instructed to remove the windows installation cd at some point (being in the last phase of the installation) and that`s when the error with the grub rescue would start- as you said, because there was no cd in. 

Any advice? Should I finally try to install Ubuntu (which now seems to be possible) and check the disk from there? Do you know if there are strong virus scanners in Ubuntu (going as deep as the boot sector)?

---

### Post by linespace on 2012-08-17
> **Codify said:**
> I agree it doesn't sound like you're booting from the CD. I've had a similar problem when trying to install Windows over a Linux install. I found that Windows didn't quite overwrite GRUB in the MBR. I had to boot up off the Windows XP disc and choose repair an installation. I ran the following commands from a command prompt: fixmbr and fixboot that did the trick and Windows booted afterwards. I've since used DBan to completely wipe the HDD of all traces of software. Fresh installs work very well then.
Hi. Thanks for the answer. The installation of Windows I got gives me no command prompt at any point- so I cannot type in the fixboot fixmbr commands you mention. I could try the DBan you suggest and rerun Windows or Ubuntu after that.

---

### Post by efflandt on 2012-08-17
Even if you change boot device order in CMOS setup, for removable media you sometimes still have to press a certain key during BIOS splash screen to select boot device (typically F12, or maybe Esc with AMI BIOS).  Then if you could boot a Ubuntu live/install CD to a live system, you could restore the mbr for Windows with:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```Assuming that the proper partition is marked as boot, which sometimes may not be the one that you think (for example Dell computers boot from their recovery partition).  But as long as nothing or nobody changed the boot partition, it may still be the proper one (grub does not pay attention to partition boot flag).

---

### Post by darkod on 2012-08-17
There are antivirus programs for ubuntu but honestly I have never used one. I don't think there are enough dangerous viruses taken into account how I use my PC (in my LAN behind the router/firewall).
And ubuntu antivirus will not be able to detect your windows virus if that's what you mean (at least I haven't heard it can do that).

Since you were seeing problems with both OSs, I would suspect hardware issue more than a virus. Yeah, surely windows can catch a virus but ubuntu very rarely, depending what you were doing with it.

If you still want a dual boot, I would suggest to install ubuntu now that you can boot the cd, and see how it goes. Don't think about viruses at first, it will be a new clean installation anyway. If it starts failing, look at your hardware.

---

### Post by CrusaderAD on 2012-08-17
If the CD drive is failing, try installing Ubuntu to a USB drive and booting to that.

---

### Post by oldfred on 2012-08-17
A few BIOS have built in checkers and consider grub a virus as it is not Windows. Check your BIOS settings. 

Users have reported these as issues:
> BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker


Also fast boot or quick boot have caused issues. Turn that off in BIOS as it is not used by Ubuntu/grub anyway.

---

### Post by oldfred on 2012-08-17
Threads merged as there were responses in both.

Please do not create duplicate threads. We all are volunteers and need to see what others have posted to not duplicate on create conflicts confusing an issue.

---

