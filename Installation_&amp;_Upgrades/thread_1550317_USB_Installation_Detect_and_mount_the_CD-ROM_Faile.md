---
title: "USB Installation: Detect and mount the CD-ROM Failed?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by glisignoli on 2010-08-10
I'm trying to install ubuntu-10.04-server-amd64 from a 2gb usb stick.
I used Universal-USB-Installer-v1.7.7 to put the contents of the iso onto the usb disc, the installer boots fine but it always fails at "Detect and mount CD-ROM". Any suggestions? I thought about trying to mount the usb stick (/dev/sdb) to the where the installer is looking for the CD-ROM but I don't really know where that is.

---

### Post by imcrazy on 2010-08-11
I just used this with a server installation from &#8220;ubuntu-10.04-server-i386.iso&#8221; on a usb stick.

In my case the commands below used
&#8220;/dev/sdb1&#8221; as &#8220;/dev/<usb drive partition device file>&#8221; and
&#8220;/mnt/iso/ubutnu-10.04-server-i386.iso&#8221; as &#8220;/mnt/usb/<iso file>&#8221;
but yours my vary.

When you get the screen with  &#8220;Load CD-ROM driver from removable media?&#8221; press ALT-F2 to get a console and enter these commands:

mkdir /mnt/usb /mnt/iso
mount &#8211;t vfat /dev/<usb drive partition device file> /mnt/usb
mount &#8211;t iso9660 &#8211;o loop /mnt/usb/<iso file> /mnt/iso

ALT-F1 to return to installation dialog and answer as follows:
Load CD-ROM driver from removable media? <No> 
Manually select CD-ROM module and device> <Yes>
Module needed for accessing the CD-ROM: none
Device file for accessing the CD-ROM: /dev/loop0

OOoops!  I realized I misunderstood your question.  My solution is for the case when you've got the iso file on the usb stick and you've booted the iso file with GRUB2.  Not the case where you've installed to a usb stick and booted from the root of the sitck. But my solution may still work for you if you put the iso file in the root directory of the usb stick.

---

### Post by wiz561 on 2010-09-10
Thanks for the tip.  I've been trying to figure this out for the past hour and this is the only thing that worked.
):P

---

### Post by shakma on 2010-09-15
imcrazy, ur the man!  This worked perfectly.  I see you're new to the forums, so thank you for making such a great contribution so soon.

Peace.
shakma

P.S.  Canonical - I love you, but you must realize people will be installing from usb drives more than CDs from this point forward.  Please update the server installer!

---

### Post by bahdom on 2010-10-27
> **imcrazy said:**
> 
mount –t vfat /dev/<usb drive partition device file> /mnt/usb

I'm getting a "device is busy" error on 10.10, which makes sense considering I'm installing from that drive.

Is there some workaround?

Thanks for your help =D

---

### Post by bahdom on 2010-10-27
> **bahdom said:**
> I'm getting a "device is busy" error on 10.10, which makes sense considering I'm installing from that drive.

Is there some workaround?

Thanks for your help =D

Re-made the image with UNet and I no longer get this error. Only now I keep getting the "Failed to copy file from cd-rom" even after following those instructions

---

### Post by bahdom on 2010-10-27
Ended up downloading 10.4 and using that instead.

If anyone knows the solution to this issue with 10.10 it would be of general interest I suppose =]

---

### Post by cfishy on 2010-10-28
Thanks a lot! I am running into the same problem with 10.0.4 LTS so i'm afraid it's not really well supported like the desktop version. I just copied the iso to a separate memory stick and mount the file from there.

---

### Post by kendallp on 2010-12-30
Figured it out.

---

### Post by jboris on 2011-01-03
I am having similar issues with installing the 64bit Server LTS version. I tried installing from the CD and it starts but fails to detect the CD Drive. So i downloaded the USB installer but now that will not let me select my RAID partition to install. It wants to install the server to the USB stick. Am I not understanding the USB Installer?
 
 
##############
Solved. Hit F6 at main install screen and selected options that caused the installer to search the entire SCSI and ATA bus for CD.

---

### Post by gzader on 2011-01-28
I think I may have found an issue here. 

I'm having the same issue with the cdrom. It's seeing the cdrom, it's mounted, but the files are bad.  Looking in /var/log sys-something I found an error looking for: 
/pool/main/l/linux/fs-secondary-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.udeb   

The issue is the file in the ISO ends with .ude not .udeb  If you look in the ubuntu iso dir:
/pool/main/l/linux/  

You'll see the file: 
fs-secondary-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.ude  

So the installer cant find that file and it fails.  I would guess that the cdrom installer knows there is a file name limit and the files match so it's all good. But with the USB stick not being a true cdrom, the inncorrect file name creates an error.   Anyway, that's my guess so far.

--- update----
So I corrected the extensions for all files in that directory. Now it installs without issue.

:)

---

### Post by Sartavius on 2011-04-26
Incorrect file extensions were exactly the problem for me. Not only did it solve the CDROM issue, but it took care of my network config problems as well! Thanks!

---

### Post by shantanubhadoria on 2012-03-08
This is wierd,
I had the same issue. I was installing ubuntu server 10.04 from a USB stick and geting the cdrom detect error. I unplugged the USB Drive and plugged it into a different USB port and it worked.
hope it works for others too.
Cheers!
-Shantanu Bhadoria

---

### Post by Bruce0 on 2012-04-24
Also had same issue, install wanted the CD.  But when I took the same image and created a USB stick instead of using a 100MB hard drive, it just worked.

Not sure if it is a bios thing or a installer thing.

Ubuntu 64 bit server 11.10

---

### Post by Ahsaniqbalkmc on 2012-07-15
I also had this issue. I followed @gzader's instructions and the error was gone. Just had to rename 5 or 6 files in the /pool/l/linux directory but it is still a pain, especially when you are a novice like me.

I hope ubuntu does something about it.

---

