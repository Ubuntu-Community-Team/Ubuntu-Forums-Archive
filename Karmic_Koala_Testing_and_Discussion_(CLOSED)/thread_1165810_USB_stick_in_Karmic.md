---
title: "USB stick in Karmic"
date: 2009-05-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Foaming Draught on 2009-05-21
I'm running the .386 daily build of May 19, and can't mount a USB stick.  The stick works fine under other distros and Windows, and worked under Karmic pre-Alpha.  I get the box message, "Cannot mount volume" ("An unknown error occurred").

Is it a corrupt /etc/fstab?  Here's fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d6933afd-222d-4d35-bfff-47f3847c9cd5 /               ext3    errors=remount-ro,relatime 0       1
# swap was on /dev/sda5 during installation
UUID=0b6a0d82-caf8-4618-b30c-a2e493bdf6d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by freeman2000 on 2009-05-21
You seem to be having a few problems with this latest update, unfortunately.  Just to respond, I don't necessarily think it's a bug.  I've also got the update, and it's mounting/reading my USB stick without problems.  Is your stick showing up in "lsusb"?  Try running that.  Wish I had a better answer for you.  Good luck.

---

### Post by Foaming Draught on 2009-05-21
> **freeman2000 said:**
>   Is your stick showing up in "lsusb"? I was going to say, "No", but actually putting the stick into a USB port helps  :redface:

Bus 001 Device 011: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

So yes, it shows up in lsusb, which I should have said in my original post.  It shows up in Nautilus, too, unmounted, but I can't mount it.

It's obviously not a bug if no-one else has the problem.  I'll wait for the next hal or kernel update, unless someone can advise me how to force mount it.

---

### Post by xens on 2009-05-21
Works for me

type the command "dmesg" after plugging your USB key, you should see something like this

> [  594.774278] sd 2:0:0:0: [sdb] 15704063 512-byte hardware sectors: (8.04 GB/7.48 GiB)
[  594.774901] sd 2:0:0:0: [sdb] Write Protect is off
[  594.774923] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  594.774939] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  594.779620] sd 2:0:0:0: [sdb] Assuming drive cache: write through

Then mount it manually for the a shell: sudo mount /dev/sdb1 (<- your device) /mnt

---

### Post by Foaming Draught on 2009-05-21
Thank you for the help xens.  dmesg returns (lots of lines ending in):

[19299.541785] usb-storage: waiting for device to settle before scanning
[19304.540200] usb-storage: device scan complete
[19304.540815] scsi 13:0:0:0: Direct-Access     FLASH    Drive AU_USB20   8.07 PQ: 0 ANSI: 2
[19304.541277] sd 13:0:0:0: Attached scsi generic sg2 type 0
[19304.577790] sd 13:0:0:0: [sdd] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[19304.578615] sd 13:0:0:0: [sdd] Write Protect is off
[19304.578620] sd 13:0:0:0: [sdd] Mode Sense: 03 00 00 00
[19304.578624] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[19304.581785] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[19304.581793]  sdd:
[19304.787053] sd 13:0:0:0: [sdd] Attached SCSI removable disk
[19308.080110] hal-storage-mou[22047]: segfault at 0 ip 0804a9f2 sp bfea78e0 error 4 in hal-storage-mount[8048000+7000]

The stick has chnaged name progressively from sdb to sdc and now sdd, but still won't mount.

---

### Post by eyelessfade on 2009-05-21
Try a reboot. Yes, yes I know. Everything can be fixed without reboot, but it sure is faster :)

---

### Post by Gina on 2009-05-21
Yes, I've often found a reboot works wonders :lolflag:

---

### Post by plun on 2009-05-21
[Unetbootin]("http://packages.ubuntu.com/karmic/unetbootin") works and can be used...

It also gives an error during start, filed [this bug]("https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/376339").

"But".... and a big one, **be careful**.... "Show all drives" must be checked and after that you can choose your stick for an output.

Blkid and vol_id has been changed in Karmic..therefore this error.

---

### Post by xens on 2009-05-21
> **Foaming Draught said:**
> Thank you for the help xens.  dmesg returns (lots of lines ending in):

[19299.541785] usb-storage: waiting for device to settle before scanning
[19304.540200] usb-storage: device scan complete
[19304.540815] scsi 13:0:0:0: Direct-Access     FLASH    Drive AU_USB20   8.07 PQ: 0 ANSI: 2
[19304.541277] sd 13:0:0:0: Attached scsi generic sg2 type 0
[19304.577790] sd 13:0:0:0: [sdd] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[19304.578615] sd 13:0:0:0: [sdd] Write Protect is off
[19304.578620] sd 13:0:0:0: [sdd] Mode Sense: 03 00 00 00
[19304.578624] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[19304.581785] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[19304.581793]  sdd:
[19304.787053] sd 13:0:0:0: [sdd] Attached SCSI removable disk
[19308.080110] hal-storage-mou[22047]: segfault at 0 ip 0804a9f2 sp bfea78e0 error 4 in hal-storage-mount[8048000+7000]

The stick has chnaged name progressively from sdb to sdc and now sdd, but still won't mount.

and what's the error if you mount the drive manually?

---

### Post by Foaming Draught on 2009-05-21
Windows habits of 5 years ago die hard, so I always try rebooting, but the stick still doesn't mount.  Other usb devices are fine.  unetbootin is no good because the stick won't mount.  The message is:

'Cannot mount volume

Error *org.freedesktop.Hal.Device.UnknownError.*'

It's my Home directory which I want to paste to this reinstalled /Home from May 19's daily build.  I can copy it to cd on another machine, and paste it from that, but I'll have to get usb sticks working anyway.  I still think that my /etc/fstab is missing a line or two (see original post), but it's an alpha after all, and I'll wait patiently for an upgrade one morning to fix it magically.

Thank you for responding, everyone who has.

---

### Post by kingborel on 2009-05-22
I'm having the same issues with SOME usb sticks (others work fine). Bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/376786](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/376786)

---

### Post by Foaming Draught on 2009-05-22
Thank you kingborel.  I might subscribe to the bug if I can work out what output Launchpad wants from me.

---

### Post by kingborel on 2009-05-22
Best bet is to replicate the error, then post the output from /var/log/syslog and/or /var/log/messages (if they vary greatly). It's at the stage where the bug just needs to be confirmed, if anything else is needed one of the more techincal people will ask for it ;)

---

### Post by Foaming Draught on 2009-05-22
The bug is confirmed, but I've joined it anyway with the output from /var/log/syslog as suggested.

As an aside, this is why I run alphas.  It would be difficult to find a less techie user than me, but I learn so much from fixing (or trying unsuccessfully to fix) the inevitable problems with early alphas.  I mean, it's not that I'm hooked on day after day of exciting updates .......  (we haven't had many for a while, come on devs, I'm breaking out in cold sweats  :)  )

---

### Post by Foaming Draught on 2009-05-24
Now here's an interesting thing.  I tried a Fedora 11 live CD (the USB stick had always shown under Fedora 10), and couldn't mount the stick.  So I tried using Palimpsest (the Gnome disk utility which is standard in Fedora 11), and hey presto, it identified that there was a mountable disk under the stick's top level, mounted it, and there is my /Home.

So I've installed Palimpsest into Karmic from Synaptic (perhaps it's gnome-disk-utility if you want to use apt-get install), and bingo, I've got my back up disk back.

I suppose I'd better append this gem to the bug report.

---

### Post by llelectronics on 2009-06-15
I did a quick and dirty build with the patch noted by priyank.(See Bug report)

As I don't have much time and I am not such a good deb builder I only patched the required files and recreated the hal package from the deb-src. I know this is not the proper way :P
It seems to work.
Here are the necessary files:

[http://www.zevenos.com/wp-content/uploads/2009/06/hal_0512git20090512-0ubuntu4_i386.deb](http://www.zevenos.com/wp-content/uploads/2009/06/hal_0512git20090512-0ubuntu4_i386.deb)
[http://www.zevenos.com/wp-content/uploads/2009/06/libhal1_0512git20090512-0ubuntu4_i386.deb](http://www.zevenos.com/wp-content/uploads/2009/06/libhal1_0512git20090512-0ubuntu4_i386.deb)
[http://www.zevenos.com/wp-content/uploads/2009/06/libhal-storage1_0512git20090512-0ubuntu4_i386.deb](http://www.zevenos.com/wp-content/uploads/2009/06/libhal-storage1_0512git20090512-0ubuntu4_i386.deb)

---

