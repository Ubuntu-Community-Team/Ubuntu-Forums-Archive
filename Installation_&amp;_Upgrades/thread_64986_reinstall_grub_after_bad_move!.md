---
title: "reinstall grub after bad move!"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by Elrohir on 2005-09-12
ok, bad move of mine... had Ubuntu on one side of the HD and installed M$WinXP on the other side...

on Ubuntu, I have sensitive info to recover...

how can I enter to Linux?

tried grub-install through the rescue option with install disk... but no luck... ](*,)

any ideas on how to acces my linux side of HD??

---

### Post by mlomker on 2005-09-12
You could boot up to a Knoppix CD (or another livecd) and mount the partition.

---

### Post by Elrohir on 2005-09-12
what if I take my HD to another PC (with Linux installed) and then mount it?

---

### Post by Elrohir on 2005-09-13
great! I could recover some info... now... HOW CAN I BOOT UBUNTU PARTITION!!! :(

---

### Post by mlomker on 2005-09-13
[QUOTE=Elrohir]great! I could recover some info... now... HOW CAN I BOOT UBUNTU PARTITION!!! :([/QUOTE]

Post the output of **sudo fdisk -l** and your /boot/grub/menu.list file and we'll see.  What is happening right now, does grub give you a menu?  When you select things what happens?

---

### Post by Elrohir on 2005-09-13
[QUOTE=mlomker]Post the output of **sudo fdisk -l** and your /boot/grub/menu.list file and we'll see.  What is happening right now, does grub give you a menu?  When you select things what happens?[/QUOTE]it would be great if GRUB was my boot loader... but it isn't... the one who loads on the MBR is the M$ boot loader...

I'm planning to reinstall Ubuntu... reinstalling keeps the /home folder I actually have or eliminates all info and makes a fresh install?

---

### Post by mlomker on 2005-09-14
[QUOTE=Elrohir]I'm planning to reinstall Ubuntu... reinstalling keeps the /home folder I actually have or eliminates all info and makes a fresh install?[/QUOTE]

If you did an automated install then your /home folder will be in the same partition as the operating system.  I ran into the same problem that you're having my first time around.

In the future I'd recommend manually partitioning your system: about 6 Gigs for the / partition (mine currently has 3 GB of files in it), about 1.5 GB for /swap, and the remainder will be your /home.  I just put everything that I can't afford to lose in /home and then I can tell the installer to just format / when I need to reinstall the operating system....I don't lose much that way.

The manual partitioning process isn't terribly user-friendly, though...

---

### Post by Elrohir on 2005-09-22
ok, been away from thread for a while... but again, if I reinstall Ubuntu, will it keep my /home folder??

and yes, /home is in the same place as /... :(

---

### Post by mlomker on 2005-09-22
>  if I reinstall Ubuntu, will it keep my /home folder??(

No.  You'll want to [back it up](http://ubuntuforums.org/showpost.php?p=361622&postcount=4) and copy it somewhere (burn to CD, FTP to a server that you have access to, whatever).

---

### Post by Elrohir on 2005-09-23
[QUOTE=mlomker]No.  You'll want to [back it up]("http://ubuntuforums.org/showpost.php?p=361622&postcount=4") and copy it somewhere (burn to CD, FTP to a server that you have access to, whatever).[/QUOTE]damn... I'll back it up...

---

