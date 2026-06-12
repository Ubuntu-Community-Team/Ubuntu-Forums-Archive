---
title: "Kernel panic - not syncing..."
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by cool_cheat on 2010-10-13
Hello everyone,
I have, for the past few days tried to install Ubuntu on an old computer i have, yet for some reason it always fails at some point.
I have tried installing the desktop 10.10 i386 version, the alternate version, the LTS version (both normal and alternate).

The error message i always seem to get stuck at is the following:

Boot from (hd0,0) ext4 bff8f0a7-f7bc-4e67-9c42-b250fcd05eef
Starting up . . .
[ 1.392055] Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0.0)
[ 1.392127] Pid: 1, comm: swapper Not tainted 2.6.35-22-generic #33-Ubuntu

I have tried installing with legacy grub and grub 2 to no avail.

I have also tried using ext3, without any success.

I have 1GB of ram with a "mobile AMD athlon MP-M 2800+" CPU (not sure about the motherboard, think it was a "pc-chips" one)

I have some knowledge in linux, though mostly from reading around, nothing too deep.

I really have no clue to why this is happening, i've even tried changing hard drives but that didn't help...

Oh, one last thing, i have checked my RAM with memtest a couple of times and it always cleared out...



Thanks.

---

### Post by mörgæs on 2010-10-14
I guess (but am not sure) that **Boot from (hd0,0) ext4 **means that you are booting from the hard drive. Have you checked the boot settings in BIOS?

---

### Post by cool_cheat on 2010-10-14
Indeed i am.
I explained myself poorly, after about 15 attempts i managed to install ubuntu on the system, however, when i try to boot the system up from the hard drive is when i get that error.

I'm sure there's more i forgot to mention, I'm rather new at this...

---

### Post by mörgæs on 2010-10-14
Now I see...

Have you tried more than one medium for installing? CD and / or a USB stick created with Unetbootin?

[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

---

### Post by cool_cheat on 2010-10-14
I have only tried installing using a CD, i will try to follow that link and install via a bootable USB.
I'll post with an update soon...

---

### Post by dino99 on 2010-10-14
[http://ubuntuforums.org/showpost.php?p=9971263&postcount=4](http://ubuntuforums.org/showpost.php?p=9971263&postcount=4)

---

### Post by cool_cheat on 2010-10-14
Thanks for the link, i'll re-format the drive and install it again via a USB drive.

---

