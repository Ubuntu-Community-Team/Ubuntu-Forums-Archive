---
title: "Help required to check my Edgy to Feisty upgrade"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2007-06-14
Bit the bullet and decided to upgrade my wife's PC from Edgy to Feisty. All seemed to be going well after the download but then 98% through the install it got stuck, from memory on the line
update-initramfs:generating/boot/init.img-2.6.20-16-generic

After several minutes I reset the PC but was unable to boot from my manual grub choice into 2.6.20-16-386. Eventually I booted up with 2.6.17-11-386 to a command line and with internet access able to update with 
sudo aptitude update
sudo aptitude dist-upgrade

After another failure to reboot with the top line of boot/grub/menu.lst showing 2.6.20-16-386 I then hashed out these entries which left 2.6.17-11-386 at the top. This is what's running now.

Update manager doesn't indicate that there's anything to update and neither does an update check with the terminal, yet I can't be on the latest kernel, can I? System Monitor shows I'm running Feisty 7.04 but with what kernel?

What when wrong with my update process? Suggestions?
Please will someone remind me of the terminal command to enable me to check which kernel version I'm using.
If as I fully suspect to be on 2.6.17-11-386 then how do I get to 2.6.20.16-386 ? Do I need to use Synaptic?
Why might I not be able to boot up with 2.6.20-386 without a crash?

Co-incidentally Restricted Drivers Manager shows that the ATI driver for the Radeon 9600 video card shows it's  a driver that's not supported. Is this relevant?

---

### Post by Handssolow on 2007-06-14
kernel version reported in Terminal with command
uname -r
As suspected mine using this PC is  2.6.17-11-386

I've updated but where's 2.6.20.-16-396 gone?

---

### Post by Handssolow on 2007-06-15
bump

Wife's Feisty PC will run with a 2.6.17-11 kernel.  Despite Synaptic showing that 2.6.20-16 has been loaded when I attempt to run with this, Ubuntu hangs and doesn't load up. Choosing instead from Grub's menu.lst  2.6.20-16 recovery and no quite splash, I read it's halting on the line about -
... waiting for root file system

Checking in the Forum I'm starting to think it might be a SATA drive recognition issue with the 2.6.20 -16 kernel.

Can someone confirm this and if so what is the solution?

Her PC has 2 HDs, primary boot from SATA with Ubuntu and Grub and secondary slave IDE with Microsooft's XP a combination which usually runs well and puts Msoft in their rightful place.

---

### Post by Handssolow on 2007-06-15
Sorry it's a one-man-band here but feel free anyone to join in.
Just Installed and successfully booted up 2.6.20-15-386 so it looks like I'm having a problem with 20-16.

---

### Post by chewie124 on 2007-07-11
I'm seeing the same behavior here too.  Grrr.

Will see if the 2.6.20-15-generic kernel works for me.

---

### Post by Handssolow on 2007-08-01
I'm have to revisiting this issue because I'm making little progress with this problem and would appreciate some further help from the Ubuntu Forum. On my wife's PC we are unable to boot up with 2.6.20.16-29 without the Ubuntu startup screen halting with the bar still  left at the beginning. My own PC with an Asus A7A266-E and IDE HD has no problem with 2.6.20-whatever.

My wife's PC has an Asus A7V800 mobo, an AMD Athlon now stable at 2.2Ghz and using 1GB ram. Its a dual boot PC with the Ubuntu on a Sata as master with GRUB. XP is on the IDE HD as slave.This system worked well with Edgy. Essentially it will run Feisty with the 2.6.20-15 kernel but not with 2.6.20-16. It hangs with 2.6.20-16 giving in recovery mode the following screen-

Beginning running /scripts/init-premount
Done
mounting root file system ... ...
Running /scripts/local-top ...
waiting for root file stystem

The system hangs with 2.6.20-16 and doesn't boot.

I've explored many postings and some Launchpad bug reports but I'm unclear as to what to do next. My view that its related to the IDE / SATA issue. I assume that I've got 2.6.20-16-29 available but why doesn't it boot up using 2.6.20-16?

Can anyone point me in the right direction for a solution?

---

### Post by chewie124 on 2007-08-01
It turned out what worked for me was to rebuild the initrd - Here's the link for it:

[http://www.ralree.info/2007/3/22/huge-mistake-in-ubuntu-feisty-fawn-herd-5](http://www.ralree.info/2007/3/22/huge-mistake-in-ubuntu-feisty-fawn-herd-5)

HTH!

---

### Post by Handssolow on 2007-08-02
Thanks chewie 124 for your reply. I'm a little hesitant in case I make a mistake with all the typing and screw up the system,  anyway I've got the following to report.

I don't know if its because of today's updates but afterwards I modified Grub to allow again 2.6.20-16 generic to show as an option and I was surprised that it booted up.

I next selected to boot 2.6.20-16-386 but Ubuntu stalled with the loading screen bar stuck at the beginning. Ctrl+Alt+F1 revealed something like this-

Check root=bootarg cat/proc/cmdline or missing modules,devices : cat /proc/modules ls/dev
Alert! /dev/disk/by-UUID/90e80c44-a31f-426e-dba6-845934594ce does not exist. Dropping to a shell

Busy Box V1.13 (Debian !:1.1.3-3ubuntu3)Built in shell/ash
enter help for a list of commands
/bin/sh:cant access tty;job control turned off

(initramfs)_

Why does the generic load but not the 386 kernel?

Suggestions?

---

### Post by Handssolow on 2007-08-02
Problem solved.  I reinstalled latest Linux-image-2.6.20.16.29-386 and was able to boot using this kernel. Not sure why it now boots. I assume all thius was caused because Ubuntu is on a Sata. Incidentally the chipset on this A7V880 is a VIA not Intel.

---

