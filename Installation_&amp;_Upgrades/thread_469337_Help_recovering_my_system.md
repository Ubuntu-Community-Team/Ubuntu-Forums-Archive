---
title: "Help recovering my system"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by yeago on 2007-06-09
Hello, first let me say my experience with Feisty can be filed under 'Nightmare'. I moved from the experiment in codebloat that calls itself Fedora to the Idealitic Ubuntu, but I've since spit out the pill.

Problem 1a: GRUB.

Since install GRUB has not worked. On start up, right after checking which device to boot from, I simply get a line: GRUB*flashing box* and hang. The only way I am able to login is to use the Rescue disk and select 'Boot from First Hard Drive'. The Fix Grub Install on the rescue disk did nothing. I've read elsewhere that people with RAID have this problem. I have no RAID array. Just the ubuntu drive and its partitions, 1 big ext3 (not working, see below) and a VFAT drive and partition.

Problem 1b: Primary partition errors after attempting to fix GRUB

I logged in and did a grub-install sdb and all was well, on restart, however, grub fails with error 15 "file not found". Using the rescue disk 'Boot from first Hard drive' command stopped working. I can login with a shell but there was apparently some problem with /sdb1, because now its read only and the mount command yields: /dev/sdb1 on / type ext3 (rw,errors=remount-ro). However, if I get a shell using the Rescue Disk it seems to mount fine, and I am able to write to the drive (but that mode is practically unusable. Can't even use VIM effectively with the shell it gives me).

Problem 2: Secondary hard drive

On startup I get a bunch of errors, none of which I can explain. I can decipher this from the mess: I/O error on /dev/sda, logical block 0. /dev/sda1, my secondary partition, does not exist. On the advice of others I used KNOPPIX to attempt to boot the drive. I was mountable and writable. Absolutely no problems.

---

If anyone could comment on any of the above problems I would be deeply grateful. I want to rescue my system to be able to move the stuff from the drive and promptly abandon Feisty. Thank you very much.

---

### Post by yeago on 2007-06-09
At this point I am suspecting user error. =)

the fact that /dev/sda1 doesn't work leads me to believe i accidentally installed grub on it, in my confusion. Still working on the problem.

---

### Post by yeago on 2007-06-09
Ok, so I've figured it out. My BIOS read the drives differently than I thought.

I've also accidentally installed GRUB to my /dev/sda, which is why it isn't working. Also, in the process I appear to have messed up my /dev/sdc, as well.

---

