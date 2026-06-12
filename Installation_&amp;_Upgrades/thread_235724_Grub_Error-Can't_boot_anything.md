---
title: "Grub Error-Can't boot anything"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by tudsy on 2006-08-13
Thought Sunday would be a nice day to try to give Ubuntu 6.06 a try. I know can't boot anything.

I started out with the following partitions (all on a single Wester Digital 160GB drive):

dev/hda1 fat32 (containing windows system stuff)
then an extended partition in NTFS (containing data, media,etc.)

I used Gparted in the Ubuntu Install program to free up some (unallocated) space from dev/hda1, then went back and selected the 'use largest free space' option from the installer menu. Everything was fine, until I tried to boot and got Grub error 17.

Now, booting from the LiveCD I get the following information when running the installer (just to see what's up, didn't do the install)

/dev/hda1 fat32 lba
/dev/hda3 ext3 boot
/dev/hda2 extended lba
/dev/hda6 linuxswap
/dev/hda5 ntfs (note, there's little exclamation point icon between 'hda5' and 'ntfs)

That's where I'm at, any help would be huge.
Thanks!

p.s.
Oh yeah,
My goal is to have a dual boot configuration with XP and Ubuntu (if all goes well, i'm not opposed to ditching XP somewhere down the road, but not yet).

And I looked through the forums, tried the suggestion of running the XP CD and trying the 'fixmbr' command, but that just seemed to make things worse.
Upon bootup I got a 'cannot load operating system' message. I reinstalled Ubuntu and am back to the Grub error 17.

Thanks y'all.

---

### Post by skale on 2006-08-13
With the Ubuntu CD in rescue mode, reinstall GRUB and see if it works.

---

