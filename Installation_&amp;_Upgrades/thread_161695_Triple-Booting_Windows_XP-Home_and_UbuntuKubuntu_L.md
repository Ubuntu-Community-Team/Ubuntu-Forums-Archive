---
title: "Triple-Booting Windows XP-Home and Ubuntu/Kubuntu Linux v5.10"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by LinNewB68 on 2006-04-17
I haven't seen a post in here about doing this yet.

I've been running Ubuntu from a Live-DVD, and I like what I've seen.

I would like to triple-boot Win XP-Home and Ubuntu/Kubuntu v5.10 (preferably both Linux's) from two separate 'physical' drives.  

I am running Win XP-Home on an NTFS C-Drive, (Primary Master), and I will be running Ubuntu/Kubuntu from an IDE FAT-32 formatted (Primary Slave), OR, the IDE FAT-32 drive plugged into a USB drive box adapter that I have (the preferred method).  I do NOT want to re-install Windows and all my apps, so I'd rather not re-partition my C-Drive, but would prefer to use a separate physical drive instead.

I thought I would format and partition the Secondary Drive-D (Slave) from Windows XP,  OR just unplug my Primary Drive C (to protect my Windows setup), then format and partition the Secondary Drive in Fat-32 with FDisk from a boot floppy, and then install Ubuntu and Kubuntu to it.

Then later I'll try to add a boot manager program, or a routine to Windows XP 'Boot.Ini' to triple-boot with.  

I know how to format/partition the drive through Windows or FDisk it with a boot floppy.

What I'm wondering is what is the best way to get them to triple-boot after installing them.  According to the book "Windows XP Secrets", you need to use a boot manager program to dual-boot with.  But the book also has a routine you can add to Windows 'Boot.Ini' to get your PC to dual-boot. 

Does anyone know if Ubuntu/Kubuntu has a boot manager that I can add to the (Windows) C-Drive to triple-boot with, or if I can get one somewhere.  Or, can I just add a routine to 'Boot.Ini' to triple-boot WinXP-Ubuntu-Kubuntu.  And any idea what routine for 'Boot.Ini' might work well.

Also, will Ubuntu/Kubuntu support a 40-Gig IDE, FAT-32, Drive-D slave, or the same drive as a USB-Box adapted IDE Drive-X?


Thanks In Advance!
:-k

---

### Post by Elvish Legion on 2006-04-17
[QUOTE=LinNewB68]I haven't seen a post in here about doing this yet.

I've been running Ubuntu from a Live-DVD, and I like what I've seen.

I would like to triple-boot Win XP-Home and Ubuntu/Kubuntu v5.10 (preferably both Linux's) from two separate 'physical' drives.  

I am running Win XP-Home on an NTFS C-Drive, (Primary Master), and I will be running Ubuntu/Kubuntu from an IDE FAT-32 formatted (Primary Slave), OR, the IDE FAT-32 drive plugged into a USB drive box adapter that I have (the preferred method).  I do NOT want to re-install Windows and all my apps, so I'd rather not re-partition my C-Drive, but would prefer to use a separate physical drive instead.

I thought I would format and partition the Secondary Drive-D (Slave) from Windows XP,  OR just unplug my Primary Drive C (to protect my Windows setup), then format and partition the Secondary Drive in Fat-32 with FDisk from a boot floppy, and then install Ubuntu and Kubuntu to it.

Then later I'll try to add a boot manager program, or a routine to Windows XP 'Boot.Ini' to triple-boot with.  

I know how to format/partition the drive through Windows or FDisk it with a boot floppy.

What I'm wondering is what is the best way to get them to triple-boot after installing them.  According to the book "Windows XP Secrets", you need to use a boot manager program to dual-boot with.  But the book also has a routine you can add to Windows 'Boot.Ini' to get your PC to dual-boot. 

Does anyone know if Ubuntu/Kubuntu has a boot manager that I can add to the (Windows) C-Drive to triple-boot with, or if I can get one somewhere.  Or, can I just add a routine to 'Boot.Ini' to triple-boot WinXP-Ubuntu-Kubuntu.  And any idea what routine for 'Boot.Ini' might work well.

Also, will Ubuntu/Kubuntu support a 40-Gig IDE, FAT-32, Drive-D slave, or the same drive as a USB-Box adapted IDE Drive-X?


Thanks In Advance!
:-k[/QUOTE]


Why not just install (k)ubnutu and install kde or gnome and run both but only take up one grub entry?

---

### Post by aysiu on 2006-04-17
It's actually a lot easier than you think it is.

First of all, you can easily install Ubuntu on the drive your XP is currently on without losing any data, but... I agree with you that it's probably safest to just use the extra drive.

FAT32 isn't going to work for Linux--Linux can use (read/write) data on FAT32, but it can't be installed to FAT32. The good news is that you can use [fs-driver](http://www.fs-driver.org/) to read/write Ext3 from Windows.

By the way, you don't need a tri-boot if you want Ubuntu *and* Kubuntu, since Kubuntu is just Ubuntu with a KDE desktop environment. You can install Ubuntu and have both KDE and Gnome on it.

So just pop in the Ubuntu installer CD.
When you get to the partitioning part, select to erase the entire D: drive... or if it doesn't have that option, select "Manually Edit the Partition Table" and resize the D: drive so that you have an Ext3 partition mounted at / and another smaller partition that's swap. (It's kind of hard to explain all this--look at [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) for more details with screenshots).

Then install Grub to the MBR (you'll be prompted for this), and you'll have your dual boot. When you reboot, you'll have a menu that'll ask whether you want to boot Ubuntu or Windows.

---

### Post by LinNewB68 on 2006-04-17
[QUOTE=Elvish Legion]Why not just install (k)ubnutu and install kde or gnome and run both but only take up one grub entry?[/QUOTE]


Well, I'm not that familiar with Ubuntu yet, especially installing Ubunto-Kubunto together.  And I know very little about Grub yet.  I'll have to read up on that.  Might work.  Thanks.

:)

---

### Post by aysiu on 2006-04-17
[QUOTE=LinNewB68]Well, I'm not that familiar with Ubuntu yet, especially installing Ubunto-Kubunto together.  And I know very little about Grub yet.  I'll have to read up on that.  Might work.  Thanks.

:)[/QUOTE] You know, the stage you're at right now, I would highly advise against installing Ubuntu.

There are these things called live CDs (they exist for both Ubuntu *and* Kubuntu). You pop them in your CD-ROM drive, reboot (assuming your BIOS is set to boot from CD before hard drive), and then you get a taste of what Ubuntu is like on your computer.

The live CD runs completely off your computer's RAM and the CD itself--it does not touch your hard drive.

Even though the live CD will run more slowly than a regular install of Ubuntu, it will also give you a good idea of how well your hardware is detected (sound, video, internet)--in other words, how many problems you'll have to come to the forums asking about how to fix.

More importantly, it's a good non-committal way of getting familiar with the KDE and Gnome interfaces and Ubuntu in general.

**Edit**: Never mind. I'm a dunce. You've been using the live DVD already! Doh!

Okay, then I would suggest just keep using it for a week or two. Seriously.

By the way, does the live DVD not have both Gnome and KDE on it? How much RAM does your computer have? If the DVD has only Gnome, and you have a lot of RAM (like 1 GB), you might be able to "install" KDE (it won't be installed once you reboot) and try it out.

---

### Post by LinNewB68 on 2006-04-17
[QUOTE=aysiu]It's actually a lot easier than you think it is.

First of all, you can easily install Ubuntu on the drive your XP is currently on without losing any data, but... I agree with you that it's probably safest to just use the extra drive.

FAT32 isn't going to work for Linux--Linux can use (read/write) data on FAT32, but it can't be installed to FAT32. The good news is that you can use [fs-driver](http://www.fs-driver.org/) to read/write Ext3 from Windows.

By the way, you don't need a tri-boot if you want Ubuntu *and* Kubuntu, since Kubuntu is just Ubuntu with a KDE desktop environment. You can install Ubuntu and have both KDE and Gnome on it.

So just pop in the Ubuntu installer CD.
When you get to the partitioning part, select to erase the entire D: drive... or if it doesn't have that option, select "Manually Edit the Partition Table" and resize the D: drive so that you have an Ext3 partition mounted at / and another smaller partition that's swap. (It's kind of hard to explain all this--look at [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) for more details with screenshots).

Then install Grub to the MBR (you'll be prompted for this), and you'll have your dual boot. When you reboot, you'll have a menu that'll ask whether you want to boot Ubuntu or Windows.[/QUOTE]



Great.  Maybe I'll try that.  But I thought I read that Linux will use Fat or Fat-32?  Interesting...

Thanks!

---

### Post by aysiu on 2006-04-17
[QUOTE=LinNewB68]Great.  Maybe I'll try that.  But I thought I read that Linux will use Fat or Fat-32?  Interesting...

Thanks![/QUOTE] Well, it can read from and write to FAT32, but it can't be installed to FAT32, especially since FAT32 doesn't support permissions on files, and Linux is completely built around permissions.

It's sort of like Ext3 for Windows. Windows (with the fs-driver linked to above) can read from and write to Ext3, but it can't be installed to Ext3. It has to be installed to either NTFS or FAT32.

---

### Post by LinNewB68 on 2006-04-17
[QUOTE=aysiu]You know, the stage you're at right now, I would highly advise against installing Ubuntu.

There are these things called live CDs (they exist for both Ubuntu *and* Kubuntu). You pop them in your CD-ROM drive, reboot (assuming your BIOS is set to boot from CD before hard drive), and then you get a taste of what Ubuntu is like on your computer.

The live CD runs completely off your computer's RAM and the CD itself--it does not touch your hard drive.

Even though the live CD will run more slowly than a regular install of Ubuntu, it will also give you a good idea of how well your hardware is detected (sound, video, internet)--in other words, how many problems you'll have to come to the forums asking about how to fix.

More importantly, it's a good non-committal way of getting familiar with the KDE and Gnome interfaces and Ubuntu in general.

**Edit**: Never mind. I'm a dunce. You've been using the live DVD already! Doh!

Okay, then I would suggest just keep using it for a week or two. Seriously.

By the way, does the live DVD not have both Gnome and KDE on it? How much RAM does your computer have? If the DVD has only Gnome, and you have a lot of RAM (like 1 GB), you might be able to "install" KDE (it won't be installed once you reboot) and try it out.[/QUOTE]


Yes, I agree.  I'm going to make sure I know what I'm doing before I install.  I have tons of experience with TI-Commodore-AtariST-Dos-Win9598XP installs and configs.  Just little yet with Linux.

I used the Ubuntu Live DVD install.  Haven't seen KDE on it yet, but maybe I missed it.  I thought we had to get that from Kubuntu?  I have a Pentium 2.8 Gig-HT. with 1-Gig of Ram, so should be fine there.  WinXP-H runs fine on it.  (if you can call the way Windows ever runs 'fine'..  haha..)  Maybe I'll try what you said, and give KDE a workout.  Or just do a KDE Live DVD.

Thanx.

:)

---

### Post by stumpadoodle on 2006-04-17
I'm actually in the same position this person is, trying to install ubuntu to a separate 40 gig IDE hard drive in my Windows XP box, with windows XP installed on my 160 gig SATA drive. I know the routine for partitioning and installing because I've successfully installed Ubuntu on a computer before, however I'm running into problems...

The first few times I tried it, it would get stuck initializing the USB devices, which is wierd, since all I have hoooked up USB are my mouse and keyboard. Then, on my recent couple of tries, it started giving me this error nonstop instead:

```
uhci_hcd 0000:00:1d.1d.1:host controller process error, something bad happened!
```

I have abslutely no idea what this means, and I can't even begin to guess what I need to do. The only thing I can say is that it started giving me this new error after I installed VMplayer on my XP installation, because I thought maybe I'd give that a try but decided I'd rather have a normal installation of Ubuntu instead.](*,)

---

### Post by LinNewB68 on 2006-04-17
[QUOTE=aysiu]Well, it can read from and write to FAT32, but it can't be installed to FAT32, especially since FAT32 doesn't support permissions on files, and Linux is completely built around permissions.

It's sort of like Ext3 for Windows. Windows (with the fs-driver linked to above) can read from and write to Ext3, but it can't be installed to Ext3. It has to be installed to either NTFS or FAT32.[/QUOTE]


Ah, that must have been what I read.  That it just 'reads' FATs.  I need to do more study on the drive-handling.  Thx for the info.

---

