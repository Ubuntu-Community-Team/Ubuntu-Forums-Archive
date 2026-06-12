---
title: "I used up 20 gigs of hard drive space installing fiesty"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2007-06-14
had install problems got it to work, but only have 14 gigs left on 40 gig hard drive. and when I boot I get the option of booting like 5 ubuntus and a pclinux i want to recover this disc space. Can someone help please? Thanks

---

### Post by dannyboy79 on 2007-06-14
are you in your ubuntu install now? I need to this info if you are

sudo fdisk -l

df -h

mount

cat /etc/fstab

---

### Post by swoll1980 on 2007-06-14
no all finished it's working fine 
i'm using it right now now, booted from hard drive

---

### Post by swoll1980 on 2007-06-14
i will try the command and let you know

---

### Post by swoll1980 on 2007-06-14
wait no i wont im not in install dah

---

### Post by dannyboy79 on 2007-06-14
ok, slow down....... you mention that you have many many ubuntu choices within your grub menu when you boot, I am asking, when you boot into the "ubuntu install" that you want to keep, please tell me what the commands return

---

### Post by swoll1980 on 2007-06-14
just fiesty nothing else

---

### Post by swoll1980 on 2007-06-14
I tried using the guided use entire disk option but it kept telling me ext3 was busy and could not be mounted, so i decieded to to some half-baked partioning (witch I have no clue how to to, and messed it up pretty good

---

### Post by dannyboy79 on 2007-06-14
you came here for help, I can't help you if you don't help me help you. are you going to post what I asked for???????????? otherwise I'll move on to help others and them someone can help you after they come to the thread

---

### Post by swoll1980 on 2007-06-14
commands for what?

---

### Post by swoll1980 on 2007-06-14
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2264    18185548+  83  Linux
/dev/sda2            4560        4863     2441880   82  Linux swap / Solaris
/dev/sda3   *        2265        4466    17687565   83  Linux
/dev/sda4            4467        4559      747022+   5  Extended
/dev/sda5            4467        4559      746991   82  Linux swap / Solaris

Partition table entries are not in disk order
Does this help at all?

---

### Post by dannyboy79 on 2007-06-14
a tiny bit but I still need the rest, why are you making this so hard for me to help you??????

---

### Post by swoll1980 on 2007-06-14
I don't know anything about cpu don't know what info you need . Pretend your talking to a retard

---

### Post by swoll1980 on 2007-06-14
Feisty is the only thing I wan't to keep I want to get rid of pc linux and the other 5 ubuntus and recover disk space thet there taking  up do you want to know whats on my grub menu?

---

### Post by dannyboy79 on 2007-06-14
i already asked for the info I needed once and I am sorry but you've worn my patience to the bone and can't continue. 

Now you may think that I am a jerk for doing this but if someone specifically states exactly what commands they want you to enter into the terminal, and then they ask for that output, and you can't even do that, than I guess if that makes me a jerk for not wanting to continue to help since it would probably take another 2 hours, than so be it.

---

### Post by swoll1980 on 2007-06-14
i thought that was if i was in the install still

---

### Post by swoll1980 on 2007-06-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9e7a3784-b668-4ca9-b1a8-8986e407ccc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=80aff299-bf47-4c7c-9114-e04951a2694f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
nolan@BIGMAN:~$

---

