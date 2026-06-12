---
title: "Install hangs on HP Pavilion a1130n"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by MarkLori on 2005-08-08
I just got a new computer.  Hooray and welcome to the world of modern cpu's!  All was fine until I came home today and decided it was a day old and needed a real OS to make the XP side jealous.  The installer for Hoary comes up fine and all seems well until it says there is no device to configure partitions on, or something to that effect.  I tried another distro and had the same kind of problem except that it failed trying to load an ATI SATA driver.  Is there a problem with SATA disks?  Something I need to do differently?   The system is:

HP Pavilion a1130n
AMD Athlon 3500+ 64 bit processor.  (I am only trying to load the 32 bit version for now)
250 GB SATA Hard disk
1 Gb Ram
ATI Radeon Xpress 200 Graphics (I hear there are problems with these in Linux, any sugestions?)

I REALLY want Linux on this box, but have never had this type of problem before.  Normally the problems start after the install is done :-P 

Thanks for any assistance.

Mark

---

### Post by nocturn on 2005-08-09
I do not have one myself, but I read there a some problems with SATA drives, specially at install time.

---

### Post by nocturn on 2005-08-09
What motherboard/chipset is in this machine?
If it is nforce4, that seems not supported yet...  Breezy might work on it.

---

### Post by MarkLori on 2005-08-09
The motherboard is a MSI RS480M2-IL with an ATI chipset.  This is apparently not an Ubuntu problem as no other distro I have will load either.  All problems point to either not loading ATI SATA drivers or not being able to resize the windows partition.  LiveCD distro's work but can't see the hard disk.  Has anyone gotten around this?  Would buying Partition Magic or something like it help?  Or will the SATA problem keep me from using the free space regardless?  It is unacceptable to be stuck without Linux!  

Any and all help appreciated!

Thanks
Mark
 ](*,)

---

### Post by nocturn on 2005-08-10
[QUOTE=MarkLori]The motherboard is a MSI RS480M2-IL with an ATI chipset.  This is apparently not an Ubuntu problem as no other distro I have will load either.  All problems point to either not loading ATI SATA drivers or not being able to resize the windows partition.  LiveCD distro's work but can't see the hard disk.  Has anyone gotten around this?  Would buying Partition Magic or something like it help?  Or will the SATA problem keep me from using the free space regardless?  It is unacceptable to be stuck without Linux!  

Any and all help appreciated!

Thanks
Mark
 ](*,)[/QUOTE]

The Ati chipset is quite new I think, chances are it is not supported (well) yet.
You might try Breezy, maybe the newer kernel works on it...

---

### Post by MarkLori on 2005-08-10
I'll find out about it and give it a shot.  I'll post back here if it works for me.  

Thanks,
Mark

---

### Post by areguly on 2005-08-10
[QUOTE=MarkLori]I just got a new computer.  Hooray and welcome to the world of modern cpu's!  All was fine until I came home today and decided it was a day old and needed a real OS to make the XP side jealous.  The installer for Hoary comes up fine and all seems well until it says there is no device to configure partitions on, or something to that effect.  I tried another distro and had the same kind of problem except that it failed trying to load an ATI SATA driver.  Is there a problem with SATA disks?  Something I need to do differently?   The system is:

HP Pavilion a1130n
AMD Athlon 3500+ 64 bit processor.  (I am only trying to load the 32 bit version for now)
250 GB SATA Hard disk
1 Gb Ram
ATI Radeon Xpress 200 Graphics (I hear there are problems with these in Linux, any sugestions?)

I REALLY want Linux on this box, but have never had this type of problem before.  Normally the problems start after the install is done :-P 

Thanks for any assistance.

Mark[/QUOTE]
 
Hi,I have one HP ze2113us, which also comes with the ATI xpress 200. It is still not supported :(

I was able to install Ubuntu on text mode, and then upgrade to the kernel 2.6.11 (atiixp module is newer and supports this board) and now everything works.

Quick notes:

DMA doesn't work on 2.6.10 because atiixp doesn't support our board, 2.6.11 and forward run fine. This could be the cause for your freezes.
Add 'atiixp' to /etc/modules and reboot. put it as the first module to load.

I had a constant 50% cpu usage even in single user mode until a passed 'noapic' to the kernel on grub. See [http://bugzilla.ubuntu.com/show_bug.cgi?id=13307](http://bugzilla.ubuntu.com/show_bug.cgi?id=13307) for my bug ticket.

The wireless works just fine, I followed this link:
[http://ubuntuforums.org/archive/index.php/t-24000.html](http://ubuntuforums.org/archive/index.php/t-24000.html)

The Video card is still NOT supported by ATI on Linux, I was unable to make it work, even though Ubuntu detects it, when I start GDM/X11 it freezes completely, edit xorg.conf and switch the 'ati' driver for 'vesa'. You'll end up with no hardware accel, but it is a pretty decent screen until ATI adds supports for this. (I tried the latest from ATI website, no luck).

I added the following lines to xorg.conf's   Section "Monitor"

        DisplaySize     270     203     # 1024x768 96dpi
#       DisplaySize     338     254     # 1280x960 96dpi
#       DisplaySize     338     270     # 1280x1024 96dpi
#       DisplaySize     370     277     # 1400x1050 96dpi
#       DisplaySize     423     370     # 1600x1400 96dpi

This will correct the screen size to 96 DPI.

Forgot to tell you to pass noinotify to kernel on grub as well, if you don't Gnome will freeze. This is a know bug on Hoary with kernels greater then 2.6.10.

---

### Post by MarkLori on 2005-08-10
Thanks!  I'll try this as soon as I get home from work.  I had no idea it would be such a challenge to get linux onto this new box.  I'll post back if this works out.  Without the hardware accel. are yu still able to get the 3D stuff to work?  It's not critical to me, but I do like a good game now and then.

Thanks,
Mark

---

### Post by areguly on 2005-08-10
[QUOTE=MarkLori]Thanks!  I'll try this as soon as I get home from work.  I had no idea it would be such a challenge to get linux onto this new box.  I'll post back if this works out.  Without the hardware accel. are yu still able to get the 3D stuff to work?  It's not critical to me, but I do like a good game now and then.

Thanks,
Mark[/QUOTE]
 
I haven't really tried, because as it came with WinXP bundled, I've made it dual boot, so when I want to play, I boot into windows and forget about these problems.

but I do get some 500-800 fps on glxgears. It works, it's slow but it works.

I really thing that it is just a matter of time until these issues get fixed but the ATI driver, at least I hope so.

good luck

---

### Post by MarkLori on 2005-08-11
Ok, some progress has been made.  I still got hung on the text mode install, so abandoned ubuntu and loaded Mandriva 2005.  Found out that I needed to go into Windows and run chkdsk /f as the drive was giving errors to the ntfsresize program.  After that it loaded ok and it has the newer .11 kernel which made all the other problems go away as they did for areguly.  I wonder if Breezy is getting to the point yet, where I could use it for most stuff or if I need to wait a little longer?  I have Hoary on this machine at work and really like it.  At home I have a  s l o w  dialup connection and need the add on cd to get a lot of the stuff I really use.  Would the Hoary add on  cd still install on Breezy?  If not. I may be forced to wati until it is stable.

Thanks for all the help.  These forums have answered many questions for me and this is the first time I've had to post!  This is another reason I love ubuntu!

Thanks,
Mark  O:)

---

### Post by areguly on 2005-08-18
[QUOTE=MarkLori]Ok, some progress has been made.  I still got hung on the text mode install, so abandoned ubuntu and loaded Mandriva 2005.  Found out that I needed to go into Windows and run chkdsk /f as the drive was giving errors to the ntfsresize program.  After that it loaded ok and it has the newer .11 kernel which made all the other problems go away as they did for areguly.  I wonder if Breezy is getting to the point yet, where I could use it for most stuff or if I need to wait a little longer?  I have Hoary on this machine at work and really like it.  At home I have a  s l o w  dialup connection and need the add on cd to get a lot of the stuff I really use.  Would the Hoary add on  cd still install on Breezy?  If not. I may be forced to wati until it is stable.

Thanks for all the help.  These forums have answered many questions for me and this is the first time I've had to post!  This is another reason I love ubuntu!

Thanks,
Mark  O:)[/QUOTE]
 Hey just to let ou know, ATI has released new drivers, and now I have Full opengl support!

Check here:

ati xpress

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

regular installer
[http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run)

you will need to linux-headers for your kernel version.

good luck

---

