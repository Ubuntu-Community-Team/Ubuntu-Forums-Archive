---
title: "kernel updates and grub"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by infoseeker on 2006-09-15
I have a seperate boot partition as I triple boot Ubuntu, Gentoo and XP.
Each time I do a kernel update I have to reconfigure grub.

Ubuntu is on hdc1
swap is on hdc2
boot is on hdc3
Gentoo is on hdc4

I must add that the original installation had boot & grub under hdc1 and the boot partition was created later.

After kernel updates grub is reset to read grub configuration on 'hdc1/boot/grub' which of course isn't there.

Any suggestions?

---

### Post by darrenst on 2006-09-15
Yes, I just had a similar thing, although I do not dual (triple?) boot.

Downloaded the kernel updates that were pushed, and when I rebooted it failed to come back up, hanging at the 'mounting root filesystem' bit.

Ran the recovery boot option to see the text version of what was happening, and found that it eventually timed out failing to find /dev/hda2.

I used to have Windows on this PC, and originally this was on /dev/hda1, and Ubuntu was on /dev/hda2 (as per the default grub config). 

When I eventually removed my Windows partition and reallocated the space, I rebuilt the PC and had the whole Ubuntu boot portion of the disk on /dev/hda1. This involved manually editing the grub config to make it boot from /dev/hda1 instead of hda2.

The recent kernel install has (bizarrely) decided to overwrite my grub.lst, so that the boot disk was my (non-existant) /dev/hda2. Also bizarrely, it left the root disk entry as (hd0,0), and not changed it to hd(0,1) to match the change to the boot disk. I noticed in a simlar post ([http://www.ubuntuforums.org/showthread.php?t=257959](http://www.ubuntuforums.org/showthread.php?t=257959)) that they thought this just affected Windows partitions, but no.

To cut a long story short, I tend to now keep a backup of the grub config file (/boot/grub/menu.lst) to fall back on if things go wrong.

Solution was to restore one of my old ones. If I hadn't had one, going through the file and replacing all the /dev/hda2 entries with /dev/hda1, as per the following:

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

Since the machine was no longer bootable, I used a livecd (happened to be the GParted LiveCD, but I'm sure any would do) to boot up, then launched a terminal.

Mounted my boot disk:

mkdir mydisk
mount /dev/hda1 mydisk

Went to the grub directory:

cd mydisk/boot/grub

Replaced the dodgy boot file with a backup:

cp menu.lst.230806 menu.lst

(Alternately, edit it and fix it as per the section I pasted earlier, disk / boot devices as appropriate).

Reboot and hey presto, back to life.

Hope this helps.

As a side issue, this is the second time in so many months that I have had to resort to stuff like this, I was affected by the non-starting X update a month or so ago, that one took me a lot longer to fix as I didn't have access to a second working PC to go on the forums and look for help. I eventually had to phone someone to do it for me and read instructions down the phone.

I would consider myself to be reasonably technically savvy being an HP-UX  software developer with a reasonable knowledge of Unix / Linux system admin. I pity a newbie with these sorts of faults...especially with the idea being that Ubuntu is the user friendly face of Linux. But then, it is free, so shouldn't moan, and extremely happy with it in general!

Cheers,

Darren

---

### Post by wkulecz on 2006-09-15
Move your /boot/grub/menu.lst file from your /boot partition to /boot/grub on Ubuntu.  Then all should be well on the next reboot after you merge in what Ubuntu needs.  

IMHO the days of needing a seperate boot partition are long gone, as grub really does work great.  Just copy your old menu.lst from the previous setup to the location used by the most recent install and merge in what was created for the new install.

--wally.

---

### Post by infoseeker on 2006-09-15
> Move your /boot/grub/menu.lst file from your /boot partition to /boot/grub on Ubuntu
After having to do this reconfigure twice in so many months, I'll move everything in hdc3 back where it was before (hdc1/boot) and remove the boot partition.  Seems to be the best way out....for now :rolleyes:  .

---

