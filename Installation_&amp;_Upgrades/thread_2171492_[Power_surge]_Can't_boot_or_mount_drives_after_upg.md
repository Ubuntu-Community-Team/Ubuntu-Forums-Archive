---
title: "[Power surge] Can't boot or mount drives after upgrade, grub gone, completely lost"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2013-08-31
I have two drives with important files on them. I thought I could upgrade one and the files would be ok backed up on the other one. They were both 12.10.

No good. Grub was updated on both, individually, a while back and they were working fine until I upgraded ONE of the drives. GRUB is nowhere to be found and the upgraded drive wants to boot from CD, which neither drive has ever done. The other one, that should be untouched, simply doesn't boot. No missing grub file error, no boot from CD message, nothing. It just hangs and never boots.

I created a live USB and have tried to boot the drives (individually) from that, but can only boot into the USB itself. Trying to install grub to the connected drive results in the following error:

Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

I tried follwoing instructions here for boot-repair:
[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

I get no errors, but nothing changes. I tried both the Recommended repair and Advanced, but the options recommended under Advanced options don't show up and therefore cannot be selected.

I also tried the method here:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UiFyf3Ygg8o](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UiFyf3Ygg8o)

I cannot complete the instructions. I get the error: 
mount: mount point /mnt/dev does not exist

When mounted, the drive disappears from the sidebar menu. I don't even know how to look at the drive to see if something is missing. I can't open it. I'm wondering if nouuid and nodev in fstab has something to do with that. I have NEVER had a problem looking at any drive from a working live CD or USB before in 6-7 years of using Linux. I don't where to go with this next. 

I'm so frustrated with Ubuntu. Every upgrade since Hardy has resulted in complete disaster, and the disasters get worse with every upgrade. 

Is there something else I can try to recover one of my drives? Please help.

---

### Post by VMC on 2013-08-31
Where's the "pastebin" output from the boot-repair?

---

### Post by Luxx on 2013-08-31
[http://paste.ubuntu.com/6046574/](http://paste.ubuntu.com/6046574/)

---

### Post by VMC on 2013-08-31
You have syslinux installed on both hard drives. Have you tried booting from a livecd and running grub-install from there?

edit: It looks like sdb is a usb drive.Are they both usb drives? Syslinux is set to boot off sdb, which is fat32.

---

### Post by Luxx on 2013-08-31
"I created a live USB and have tried to boot the drives (individually) from that, but can only boot into the USB itself. Trying to install grub to the connected drive results in the following error:

Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting."

Yes, sdb is the Live USB. Syslinux is set to boot off the USB and I can't seem to get anywhere with booting either of the hard drives.

I disconnected that drive and connected the other one and tried to run boot-repair again, but it would only give my the option to  create a boot info summary. It didn't do anything. 

[http://paste.ubuntu.com/6046794/](http://paste.ubuntu.com/6046794/)

"=> No boot loader is installed in the MBR of /dev/sda."

I don't understand this at all... this is the drive that I booted from ONCE after the upgrade when I couldn't boot the other drive on it's own. Then when I went back later to look at things I couldn't boot from this one either.

Holy crap... according to GParted the entire disk is unallocated. I have no idea how that happened. The other one looked like there was a file system on it though. There should be file systems on them both.

Please note:   I only have ONE of the hard drives connected inside the computer at a time. The drive showing as sdb is the Live USB in both cases.

---

### Post by Luxx on 2013-08-31
Well, since the OS is obviously dust on the second hdd I might as well install from the live USB.... at least then I might have one working hard drive for the time being. Hopefully I will be able to recover the important files from the other one, if I can't get it to boot.

---

### Post by westie457 on 2013-08-31
Hi Luxx this is one part of your last Bootinf script that is worrying > [COLOR=#000000]Disk /dev/sda doesn[/COLOR][COLOR=#BB4444]'t contain a valid partition table[/COLOR]
There is a couple of others but they are related to this one.

Have you thought about using Testdisk. It is available in the repo's. This link will give more information. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Hopefully you get this before you reinstall.

---

### Post by Luxx on 2013-09-22
Yes, one of my drives mysteriously lost the filesystem. It seems to have been a gradual disintegration. The other one shortly followed. I tired restoring, but ended up not being able to boot anything. Eventually I couldn't even boot into my flash drive. At that point I started thinking the motherboard had issues as well.

I'm not entirely sure, but I think it had something to do with an electrical surge that reportedly shorted out the entire house when a new electircal line was put in. This would have happened the same day things started getting weird. When I took the computer out of the corner it was in shortly after your last post, I noticed the case was vibrating. It was turned off and disconnected from everything. Three weeks later it still vibrates for no apparent reason, so I'm chalking it up to electrical damage. It looks like I'm starting all over again, including a new case. No sense putting new hardware in an electromagnet.

---

