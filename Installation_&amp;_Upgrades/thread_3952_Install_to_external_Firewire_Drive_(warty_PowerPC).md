---
title: "Install to external Firewire Drive (warty PowerPC)"
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by gregburd on 2004-11-10
I tried to install warty to an external Firewire drive hooked up to my PowerBook G4 17".  Everything *but* the installation of the boot loader worked like a charm.  After the install process finished up I rebooted the machine, held down the "option" key and I got a list of bootable drives that did *not* include the external Firewire drive.  This didn't surprise me due to the error metioned above.

My question is, has anyone been able to install Ubuntu to an external Firewire device and successfully boot/run from that drive?  If so, how?

Am I simply trying to do something that isn't supposed to work?

thanks in advance for any help,

-greg

---

### Post by avallon on 2004-11-10
If you find a correct way, it would be nice to know.
The similar procedure would hopefully work with any other USB external hard drive.
I would like to boot Mandrake 10.0 from external 40GB 2.5¨ notebook hard drive which is placed in Chronos external casing. I was hoping to do the same as Mandrake did with Traveller.
I tried to use Boot Magic, but the program doesn´t recognise any external hard drives.

---

### Post by merper on 2004-11-11
I want to install ubuntu ppc to my usb external hard drive too. I love mac os x, and have considered trying out ubuntu, so this way it is foolproof. If anyone could help out, I'd love it. 

Thanks
the evil merper

---

### Post by Cloudane on 2004-12-25
I've got it almost working from USB, but just not quite :)  No luck with firewire at all yet.  I got it starting to boot from USB with help from:
[http://131.204.27.45/ydl-howto/](http://131.204.27.45/ydl-howto/)
and:
[http://lists.debian.org/debian-powerpc/2001/12/msg00072.html](http://lists.debian.org/debian-powerpc/2001/12/msg00072.html)

After installing (yaboot install failed blah blah) I booted to the install CD again and after following the first couple of questions about country etc, hit ctrl-cmd-F2  (ctrl-cmd-fn-F2 held *in that order* on a PB) to switch to the second console.

From there..

#mkdir hd
#mount -t reiserfs /dev/discs/disc1/part4 hd   (switch reiserfs for ext3 as necessary and part4 for whichever partition your linux root is on)
#chroot hd
#mount proc
#mkofboot /dev/sda2  (or wherever boot partition is)
#pico /etc/yaboot.conf

with the following config:
      ofboot=usb1/disk@1:
      init-message="You know the drill\n\n” 
      partition=4 
      timeout=30 
      install=/usr/lib/yaboot/yaboot 
      magicboot=/usr/lib/yaboot/ofboot 
      default=linux 
      image=/boot/vmlinux
      label=linux 
      root=/dev/sda4 
      read-only 
      initrd=/boot/initrd.img
      defaultos=linux 
      delay=10 
      enablecdboot 

(Save and exit)

#ybin -v --boot /dev/sda2 --config /boot/yaboot.conf

Then reboot, holding down cmd-opt-o-f.  At the firmware prompt:
boot usb1/disk@1:yaboot

This got it booting.  Unforutnately half way through it says /dev/console: no such file or directory and the kernel panics.

It's a start anyway, even though it's USB and not FW :)

---

### Post by andy_stenger on 2005-03-27
Tried to install debian sarge on a PowerBook G4 17" (2004 model) on an USB external drive today and I am finally giving up (for now). But I'd like to drop a few notes that may help others:

too boot from the CD this key-combo worked for me during power on:
shift-alt-apple-Backspace

alt is probably also called option and apple probably also command key. I always get confused about these apple special keys, sorry.

(do not use ctrl, too, or MacOS X starts in safe mode)

The debian installer of course also told me that it could not install yaboot.

To get a _usable_ shell use the one the installer offers and do:
chroot /target

or if you reboot a couple of times and use Cloudane's mount:
chroot hd

after that following Cloudane's description worked nicely for the commands. (There's one typo: use #ybin -v --boot /dev/sda2 --config /**etc**/yaboot.conf instead of #ybin -v --boot /dev/sda2 --config /boot/yaboot.conf)

Then the reboot, using alt-apple-o-f to get into the firmware menu. But I couldn't kick-off the boot command. It looks like my USB is still inactive at that level and only switched on during a later phase in the (apple) boot process.

Who ever is trying to get it to run: Good Luck!

Andy

P.S.: my external drive is a firewire/usb Mapower MAP-KC21C1G combo. The firewire install procedure kind of hangs, e.g. during disk format. It's either broken, or a buggy firewire-chip or a buggy kernel, I don't know. USB works fine, though.

---

### Post by interrupt on 2005-04-26
I have been able to boot of an external firewire drive (+ G4 iBook)

[see here](http://www.ubuntuforums.org/showthread.php?t=29837)

---

### Post by king_arthur on 2005-09-13
Well, after quite a bit of investigation, I realize that there is a recognized bug, either in Yaboot or the installer that prevents writing the bootloader correctly.

I have done some experimenting myself and have made a bit of progress.

After the Breezy installer (built 8 september) hangs, I tried booting from live CD (hoary) and waited for the Yaboot menu to appear: typing fw/node/sbp-2/disk@0:3,/boot/vmlinux starts loading the kernel into the system. Great!

Unfortunately, after a few seconds further on into the boot process, I get a kernel panic which, more or less, says:
[Cannot open root device "sda2"] which understandable as it should be in artition 3, not 2.
A few lines further I get [kernel panic - not syncing;VFS rebooting (0,0)]

Any clues as for what is wrong here?


Thanking in advance

---

### Post by rbiggs on 2005-12-14
Hi folks.

I'm also interested in figuring out how to install Ubuntu on to an external firewire drive for and iBook, but my situation is a bit different from the rest of you. My external firewire drive is partitioned. I therefore want to put Ubuntu on one of the partitions. The install cd does indeed see my external firewire drive, but the only options I seem to find in the installer is to wipe out the entire hd, not what I want to do. None of the partion options seems to see the partions on the external firewire drive. All partitions are in hfs+. I do have Ubuntu running fine on a internal partition of my iBook where it lives happily with OS X. How do I proceed to identify the partitions on the external firewire drive?
Just so you know, using df and pdisk on OS X, I'm looking at:
Internal HD:
OS X -- /dev/disk0s3
Ubuntu -- /dev/disk0s4
External HD:
/dev/disk1s3
/dev/disk1s5
/dev/disk1s7
/dev/disk1s9
/dev/disk1s11
I would like to be able to install Ubuntu into either partition /dev/disk1s3 or /dev/disk1s5.

---

### Post by king_arthur on 2005-12-14
Hi rbiggs,

I have since than changed my own setup which is now more similar to yours with one partitioned (ext3/hfs+) external firewire drive.

The problem is that Ubuntu apparently ships without kernel support for firewire.
There are several workarounds for it but only [this one]("http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html") worked for me (almost) out of the box.

Beware, however, that if you update your (working) ubuntu install, the packet manager will load and install a new kernel image with again the same problem.
You either compile a new one with f/w support and make sure it does not get updated or you change the simlinks from /boot/vmlinux to point to vmlinux-2.6.14.2 which is the working one.

Also pay attention to your openfirmware paths to your external disk which might differ.

Good luck.

/Pieter

---

