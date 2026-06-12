---
title: "clean XP install no longer boots after Ubuntu and GRUB..."
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by scotty on 2004-12-03
Hi folks,

I love this new distribution and it is just the thing to get me back to Debian after a long absence.

I recently popped a newly acquired 60gb Western Digital drive into my P4 Gigabyte motherboard based machine.  I installed WinXP first leaving half the disk unpartitioned for Ubuntu.  I installed Ubuntu, and all was well with XP and GRUB for about a week.

Last night when I arrowed down to boot into XP for some gaming I got the usual "chainloader +1" screen--but no Windows boot.  Just a seeming lockup.

I tried a fixmbr command from the WinXP installl disk and nothing loaded at all at Grub.  I got "error loading operating system".

I reinstalled WinXP from scratch and got the same error upon the initial reboot.

I tried a Smart Boot Manager floppy and WinXP STILL would not boot.

I used a Slack 10 boot floppy to get back into Ubuntu and ran grub-install.  Now I am back to square one and WinXP still does not boot.

I am really stuck.  It SEEMS like a geometry thing...But why would both OSes be fine for days and then WinXP would crap out like that?  I tried adjusting the BIOS infomation to LBA and that had no effect.

What else can I do?  Why would a brand new WinXP install fail to boot?  Plus, how can I make an Ubuntu boot floppy as I would like to avoid using a bootloader in the future?

Thanks,
Scott Strungis

---

### Post by deception on 2004-12-03
Try setting your HD to LBA in the BIOS.

---

### Post by scotty on 2004-12-03
I did try that.  It resulted in the same seeming freeze for the WinXP end of GRUB.  Without GRUB it tells me that there's an "error loading operating system".  I got that upon the initial reboot into WinXP after the install.

Scott

---

### Post by gheorghe_pop on 2004-12-03
you could reinstal grub...
try a google for the thing
 :D

---

### Post by scotty on 2004-12-03
I tried that as well.  I ran the grub-installer from within Linux after getting it to boot (poorly) from a Slack 10 boot disk.  No joy on the Windows side of things at all.

Scott

---

### Post by Original Brownster on 2004-12-03
Sounds nasty, I think you need to boot with a rescue disk and do a disk scan to check for bad sectors and hope it doesnt find a damaged boot sector.

This article might be of help:

[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)

---

### Post by wallijonn on 2004-12-05
[QUOTE=scotty]Why would a brand new WinXP install fail to boot?  Plus, how can I make an Ubuntu boot floppy as I would like to avoid using a bootloader in the future?[/QUOTE]

Windows could have changed the MBR, especially if you installed Norton Anti-Virus. For all I know WXP SP2 may touch the MBR.

I wrote up a HOWTO on how to format a floppy and copy your Ubuntu files to the floppy so that it will boot into GRUB. 

After you tested the floppy you could then re-install WXP and it will re-write the MBR. Is there any way in which you can check to see if the ACTIVE bit is set via a W98SE or DOS fdisk? 

Some users are switching to LILO instead of GRUB. Check out all their threads to see how they are faring with the boot problem.

---

### Post by CrippledFsck on 2005-02-01
OK, I am going to throw in my $0.02... I  Have been using Linux and Windows dual booting since Mandrake 6.9. I have used Suse, Novell, Slackware, Debian(woody) and never had any problems booting. Last year (2004) I decided I was not going to use Windows any more and installed Gentoo, which has been working fine since I installed it.  Last week my wife decides she wants to use Turbo Tax so I made backups and formatted my entire HD (60G Maxtor) and did a fresh install of WinXP + SP2; I then installed Ubuntu. When I tried to boot back into XP I get the following on the screen (grub is installed to the MBR):
```
rootnoverify(hd0)
makeactive
savedefault
chainloader +1
```
And then a flashing cursor and the pc does nothing. I booted off the XP CD-ROM and ran the recovery console. I ran the fixboot program and the fixmbr programs and now after booting all I get is :
```
Verifying DMI Pool Data...Error Loading Operation system.
```

According to Microsoft the only resolution is to upgrade your BIOS: [http://support.microsoft.com/?kbid=326676](http://support.microsoft.com/?kbid=326676)

I also found someone on experts-exchange.com [http://www.experts-exchange.com/Storage/Q_20829132.html](http://www.experts-exchange.com/Storage/Q_20829132.html) with the same problem and the solution was to boot from a Win98 boot disk and run fdisk /mbr. I will be trying this when I get home from work and will let you all know if it fixes the problem.

I have also installed Ubuntu at work and do not have this problem with Win2k + SP4.  Grub detected the Windows partition and works like it should.

Crippledfsck

---

### Post by CrippledFsck on 2005-02-01
Ok, well everyone can now say "I told you so"... After spending approximately 2 hours trying to find a bootable Win98 ISO (my pc does not have a 3.5 drive)  I decided to follow your advice and changed the HD Access mode from "auto" to "LBA" and WindowsXP now works. I guess the next step is to make a ghost image and then see if I can get Ubuntu installed again. I was starting to like not seeing the little "flying" windows... 

P.S. Ubuntu is impressive, and I like what I have seen so far.

CrippledFsck

---

### Post by Shadow Skill on 2005-02-06
[QUOTE=CrippledFsck]Ok, well everyone can now say "I told you so"... After spending approximately 2 hours trying to find a bootable Win98 ISO (my pc does not have a 3.5 drive)  I decided to follow your advice and changed the HD Access mode from "auto" to "LBA" and WindowsXP now works. I guess the next step is to make a ghost image and then see if I can get Ubuntu installed again. I was starting to like not seeing the little "flying" windows... 

P.S. Ubuntu is impressive, and I like what I have seen so far.

CrippledFsck[/QUOTE]
 ```
Verifying DMI Pool Data...Error Loading Operation system.
``` I got the same exact error with the 64bit ISO however I noticed that after a sucessful install Windows was not added to the bootloader menu [it was installed to the MBR.]  What made it not add xp to the bootloader at all, was it the whole lba thing not being setup right? after restoring the mbr to windows only I got the error above.

---

### Post by carlc on 2005-02-06
I followed this advice from a previous thread and got xp to boot on my system. However, your may have a different problem if you could boot to xp initially.

> Sounds like the drive geometry issue has hit you. Was thought to be
fixed in Warty, but seems like it still shows up for some people for
some reason (me included). See
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1566](https://bugzilla.ubuntu.com/show_bug.cgi?id=1566) .

A long explanation of the cause and a fix is here:
[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/) . While referencing Fedora, it applies to
Ubuntu as well. The core of the repair is here:

1) Try changing from AUTO to LBA mode in your BIOS for your hard drive.

2) Follow the instructions in the LWN article and use the sfdisk -d
/dev/hda | sfdisk --no-reread -H255 /dev/hda commands to reset the drive
geometry.

No promises that this is your problem, but if it is, one of the two
above should work.

HTH,

Bob


---

### Post by thestarman on 2005-02-07
[QUOTE=carlc]I followed this advice from a previous thread and got xp to boot on my system. However, your may have a different problem if you could boot to xp initially.[/QUOTE]
 Ugh!  People with boot-up problems after installing Linux seem to be jumping on this 'drive geometry' issue just like most DOS/Windows users used to immediately cry "virus" for all their problems!  UNLESS you are using Linux's Parted to re-size your Windows partition(s), you really shouldn't have a 'geometry problem'!  It may be possible that there are some other actions that cause this as well though, but the key factor to ask would be this: Why would your Linux install process need to change the 'geometry' of the whole disk, especially your Win partition(s)?!

   From what I can tell in the comments by the originator of this thread, he was running his HDD on a machine with a BIOS that couldn't see the real size of the drive... probably limited to only 32/33 GB; if that.  Sometimes there are people here booting up 100 GB+ drives (don't know how) on machines so ancient they can't see more than only 8.4 GB or so!!  The main reason they don't know there's a problem is because Win XP/2000 boots up from within that part of the drive that the BIOS can see, and then adds code to the BIOS in memory enabling it to access all of the drive.
   Apparently, there are some cases where GRUB is *not* using LBA access and falls back to only using the data from the BIOS... in those cases, GRUB cannot access Linux (nor Windows) if it can't see all of the partitions or at least where it needs to send execution to next.  There is a "force LBA" command for GRUB that *might* help; not sure.  Sometimes you just can't get to where you want without buying a new machine or FLASHING (if you can) your BIOS chip.

   These issues concern the broader problem of trying to use outdated BIOS code/hardware with the latest HDDs being made, going beyond the normal scope of solving problems with a particular distro of Linux trying to conform to dual booting with a completely different OS and still doing a very good job of it.  Bravo to the Ubuntu community for still helping those with a problem that's often due to hardware not up to minimum requirements or conflicts and that other OS company!

The Starman.

---

### Post by carlc on 2005-02-07
Not sure why I am being quoted in reference to,

> 
Ugh! People with boot-up problems after installing Linux seem to be jumping on this 'drive geometry' issue just like most DOS/Windows users used to immediately cry "virus" for all their problems!

All I said was, 

> 
I followed this advice from a previous thread and got xp to boot on my system. However,_ you may have a different problem_ if you could boot to xp initially.


I don't do bandwagons, yours or the "drive geometry" one, and I can boot xp now.

---

### Post by Shadow Skill on 2005-02-08
Hmm since when is a nforce4 ultra socket 939 amd 64 ready motherboard with pci express and an ati x600 PCIe gpu "outdated?"  For that matter since when is my Logitech mx duo for bluetooth "outdated?"  This Keyboard has so many problems with Linux in general when it works it works great but I constantly have to pray it will be detected upon booting the system, I wish Logitech would either make Linux drivers [If they have please point me to them.] or whoever codes the Linux kernel would fixx the broken usb modules that seem to be causing the problem.  Anyway I just flashed my motherboard which is about a week out of the box and I am about to try installing Ubuntu again, I hope forcing LBA works as I would like to try out a 64bit OS without waiting another two months or so for a stable fc4 to come out.

Update:

The LBA fix did work for me I just had to edit grub so windows would boot, everything works as far as that goes, now to get sound working in Ubuntu.

---

### Post by Tichondrius on 2005-02-08
[QUOTE=wallijonn]Windows could have changed the MBR, especially if you installed Norton Anti-Virus. For all I know WXP SP2 may touch the MBR.

I wrote up a HOWTO on how to format a floppy and copy your Ubuntu files to the floppy so that it will boot into GRUB. 

After you tested the floppy you could then re-install WXP and it will re-write the MBR. Is there any way in which you can check to see if the ACTIVE bit is set via a W98SE or DOS fdisk? 

Some users are switching to LILO instead of GRUB. Check out all their threads to see how they are faring with the boot problem.[/QUOTE]

OMG, people are still using floppies ?!  let's move on to a more reasonable approach:

1. Goto knoppix.org, download the knoppix live CD image file, and burn it onto a blank CD. This will enable you to boot into a linux OS, which contains all the tools you'll need to fix the hard drive.

2. Boot the konppix CD.

3. Check your partition table by openning a terminal:
# sfdisk -V -l /dev/hda
this should show the partition table.

4. I recommend to try and re-install grub, for example if your Ubuntu partition is /dev/hda2 and windows /dev/hda1), do this:
# mount /dev/hda2 /mnt/hda2
# grub-install --root-directory=/mnt/hda2 /dev/hda

5. Check that grub's menu.lst (it would be /mnt/hda2/boot/grub/menu.lst in the example above) file includes an entry for windows:
title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1

6. Boot the hard disk, and hopefully grub will be able to load windows.

7. If not,you'll probably have to re-install windows, but before you do, you should backup any files you need, in case they get deleted during the re-installation. Boot knoppix again, and try to mount the windows partition:

# mount /dev/hda1 /mnt/hda1

Now you can copy any files you need, or even backup the whole partition into a tar file !

8. Re-install windows into the same partition, but tell the install program not to format the partition.

9. Hopefully windows can now boot (without grub). If you want Ubuntu back, you'll have to re-install grub again....

---

