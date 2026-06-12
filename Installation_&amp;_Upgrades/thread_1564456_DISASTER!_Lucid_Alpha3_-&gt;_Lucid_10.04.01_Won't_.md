---
title: "DISASTER! Lucid Alpha3 -&gt; Lucid 10.04.01 Won't Boot"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by Rising Eagle on 2010-08-30
Updated Lucid Alpha 3 to Lucid 10.04.01 using Synaptic Package Manager (was this a mistake - is update manager different?) by pressing "Mark all for upgrades" button. Before proceeding, I cleaned out local and obsolete packages (which included 4 older kernals) as recommended online. Ubdated burg to show accurate boot menu. Rebooted several times before updating to prove that system was still intact. Burg boot menu now showed only Linux 2.6.32.22-generic and its recovery mode as options. During update, when grub and burg were asking, I told it to keep old config file (was this a mistake?). Rest of update proceeded automatically and w/o errors. Now burg shows four options Linux 2.6.32-24-generic, ...-22-generic, and their recovery modes. None boot; they all hang with errors:

For Linux 2.6.32-24-generic and its Recovery mode I get:
VFS: Cannot open root device "sda1" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
0b00  1048575 sr0 driver: sr
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

and hangs right here.

For Linux 2.6.32-22-generic and its Recovery mode I get:
udevadm trigger is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
ALERT! /dev/disk/by-uuid/)fe9a78e-....e27b does not exist. Dropping to a shell

The shell is BusyBox v1.13.3 and it does not have access to the files on the hard drive (maybe it does, I just don't know how). It gives me the prompt (initramfs) and I am clueless.

I found this: [http://ubuntuforums.org/showthread.php?t=1238771](http://ubuntuforums.org/showthread.php?t=1238771)
and it says:

Here is the solution I came across after some googling:

Problem solved:

The work around is following (thanks to <slangasek>)
(re)Start computer
If you have grub2 installed, you need to hold down the shift key while booting. If you have grub1 installed, you need to hit escape.
Now you can select the older kernel version from the grub menu
The system will boot normally.
Now open a console and run root command:
sudo update-initramfs -u
that will regenerate the initramfs for the newest kernel,
and after reboot all will work in the newest kernel also.
from [https://bugs.launchpad.net/ubuntu/ka...pt/+bug/453678](https://bugs.launchpad.net/ubuntu/ka...pt/+bug/453678)

How can I sudo update-nitramfs -u if I can't boot up recovery.

Please help. Thx.

---

### Post by surfer on 2010-08-30
you can boot using the install cd. mount the necessary disks and run update-initramfs from there.

i like the ubuntu-alternate cd as rescue cd.

---

### Post by Rising Eagle on 2010-08-30
I created a 10.04.1 cd and it fails to boot

I choose Try Ubuntu w/o Installing, it runs plymouth, then drops into BusyBox v1.13.3 and says:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

What now?

---

### Post by Rising Eagle on 2010-08-30
Found this from 2006 at [http://www.debian-administration.org/users/bacula/weblog/2](http://www.debian-administration.org/users/bacula/weblog/2)

If the following is what is happening, it should have been fixed by now. If the issue is that update-initramfs -u isn't run automatically whenever a kernel is updated, that is a problem that also should have been fixed by now. The same symptoms were reported way back in Jaunty.


There's a problem with udev on Debian that can bite you on a kernel upgrade or even on a fresh install. Basically, hard drive partition device names aren't persistent enough across kernel+initrd changes. I have seen a PATA system where the installer generated an /etc/fstab file with "/dev/hda" names, but the installed kernel booted and told udev to generate "/dev/sda" device nodes. This also happened to me when I upgraded a fresh Etch install to Lenny. Ubuntu Feisty also has the problem. 

The symptom is the system hangs during boot, "waiting for root file system." But the root file system device node passed in from /boot/grub/menu.lst never gets created because udev created a different name instead. After a while, the boot script gives up and falls back to the busybox shell in initrd. You get a prompt, "(initramfs)", that doesn't mean anything to a newcomer. 

IF you know what's happening, you can change $ROOT to the right name and exit busybox (how does that work?) and your system will boot, sort of. But your other partitions will have wrong names too. Correcting $ROOT is not enough. 

You could boot from a rescue disk and run update-initramfs. But that would copy the newly erroneous /etc/fstab into your initrd and you wouldn't be any better off. 

The best workaround I've found is to label all file system and swap volumes, and replace all the /dev/[hs]d* filenames in /etc/fstab and /boot/grub/menu.lst with labels. Then you can still boot when kernel+hotplug+udev gets the names wrong. 

  for i in hda1 hda3 hda5 hda6  # or whatever partitions you use
  do
    e2label /dev/$i ide-$i
    perl -pi -e "s,/dev/$i,LABEL=ide-$i," \
      /etc/fstab /boot/grub/menu.lst
  done
  swap=hda2  # substitute yours
  swapoff /dev/$swap
  mkswap -L ide-$swap /dev/$swap
  perl -pi -e "s,/dev/$swap,LABEL=ide-$i," \
    /etc/uswsusp.conf
  update-initramfs -u -k all


It's hard to believe this one evaded testing. Debian QA is pretty good. And it's not really a Debian-specific problem, it's a tricky spot in udev. But if you don't believe it, google for "waiting for root file system" and look at all the people asking WTF, in Linux forums all over the place, and not getting good answers.

---

### Post by Rising Eagle on 2010-08-30
My system is working again, but not with the new kernel. Using the Lucid Alternate install image, I burned a CD and booted. In recovery mode, I used the following shell commands

cd /boot
update-initramfs -u -k all

My old kernal worked, but linux-image-2.6.32-24-generic still failed as described above. I have since used Synaptic Package Manager to remove it. I then used terminal to execute the shell commands

cd /boot
sudo update-initramfs -u -k all
sudo update-burg

and all is well.


Clearly 64 bit Lucid 10.04.1 LiveCD is fatally flawed (won't boot) and must be fixed and 64 bit linux-image-2.6.32-24-generic is fatally flawed and must be avoided. Additionally, update-initramfs -u -k all should be automatically run whenever a kernel is (re)installed, updated, or repaired.

---

