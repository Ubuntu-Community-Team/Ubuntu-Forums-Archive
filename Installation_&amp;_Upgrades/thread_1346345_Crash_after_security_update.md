---
title: "Crash after security update"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by toddq on 2009-12-05
So I just installed a new linux security update and now when I reboot I get a beta prompt that asks me to insert a word.  I'm on a Windows dual boot installer Ubuntu 9.10 that I installed a few days ago.  Any suggestions.  The Windows part of the machine is working fine but the Ubuntu part seems to have been fried with the "security update."

---

### Post by mikewhatever on 2009-12-05
What's beta prompt? beta>? beta$? Can you boot the previous kernel? What about the recovery mode?

---

### Post by toddq on 2009-12-05
i found a forum discussion relevant my issue and there is a bug report.  However, no adequate solution is mentioned. I seem to have the first report of a problem with linuz-2.6.31-16-generic which allegedly included several "fixes."

 I was able to recover most everything following the ubuntu instruction [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) section on 

How can I access my Wubi install and repair my install if it won't boot?

Unfortunately, this section is incomplete.  that is it tells you how to access the install but doesn't tell you how to repair the grub.  The instructions are also rather terse and therefore difficult to follow in several places.  My additions are in parentheses.

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

(go to the terminal prompt and don't change directories. The "win" may be something else (e.g., WIN7). Click on Places and you should see something that refers to your windows drive.  Replace the above "win" with that.)

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

(cd /vdisk/boot how can then go to your boot file and find out if you don't know already what version of linux you have (e.g., vmlinuz-2.6.31-16-generic. Next, sudo gedit /vdisk/boot/grub/grub.cfg and write down your menu entry information.  You can use this information to try the following when you reboot into wubi ubuntu.  Note your values for (hd0,2) and sda2 and may be different.

sh:grub> insmod ntfs
         set root=(hd0,2) 
         loopback loop /ubuntu/disks/root.disk
         set root=(loop0)
         linux /boot/linuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
         initrd /boot/initrd.img-2.6.31-16-generic
         boot

If this works then everything should load
Next go to [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169) and apply Mark Abene's patch and his procedures.  There is also a laundry list of things in the bug report that you can try that are similar to what I've suggested.  However, I haven't been able to get the thing to boot properly and no one has figured out what is causing the problem, although this is now a confirmed bug.

There are several things I haven't figured out yet; how to give myself more space or transfer to a regular dual boot which from what I've read appears to be the best solution for my problem.

---

