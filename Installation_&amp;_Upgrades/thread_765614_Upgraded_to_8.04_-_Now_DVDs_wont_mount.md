---
title: "Upgraded to 8.04 - Now DVDs wont mount"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by TheAbz on 2008-04-24
I upgraded from 7.10 to 8.04 today via a network install. Well I did a clean install of 8.04.
When i insert a DVD into my drive i get the error as in the attached screen shot.
If i insert a normal CD then it mounts itself and works just fine. Its only with DVDs that i seem to be having a problem with. 
Reading through the forums i think it might have something to do with HAL - is this right?
I also enclose a screenshot of my /etc/f.stab

Thanks

---

### Post by Rubadubdub on 2008-04-25
Hi,

I have acactly the same problem, see my tread for details:
[http://ubuntuforums.org/showthread.php?t=767278]("http://ubuntuforums.org/showthread.php?t=767278")

CD's work DVD's don't.

I'll join you in the search for an answer to this strange problem.

---

### Post by Pumalite on 2008-04-25
You have /dev/scd0 and /dev/scd1. Check on that

---

### Post by Pumalite on 2008-04-25
This is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=679f828a-c798-4e3c-85db-5ac075588271 /               ext3    errors=remount-ro 0       1
# /dev/sdc2
UUID=d7613213-0687-4000-a4ba-6fef1a95d082 /home           ext3    defaults        0       2
# /dev/sda1
UUID=435151c5-e8ce-4a6f-96eb-6164051106d3 /media/sda1     ext3    defaults        0       2
# /dev/sda2
UUID=b468ade2-317e-4c83-b6ab-89b77cf47215 /media/sda2     ext3    defaults        0       2
# /dev/sdb1
UUID=acca6b3f-c848-47fe-bdde-34ce89d41bb1 /media/sdb1     ext3    defaults        0       2
# /dev/sdb5
UUID=55b5e787-36bb-4119-b623-12f4076d7a52 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Rubadubdub on 2008-04-25
that's right
/dev/scd0 is the DVD-writer
and 
/dev/scd1 is the DVD-reader

---

### Post by Pumalite on 2008-04-25
Funny; I have /dev/scd0 for everything.

---

### Post by ruckstande on 2008-04-26
Is anyone going to answer this question? I see this coming up a lot right now. I'm having the same issue. I installed from a DVD and everything went great. My previous 7.10 installation was fine but now I can't get the DVD to mount.

---

### Post by Rubadubdub on 2008-04-26
An additional problem in my case (see thread-link below) is that once a video-DVD is mounted with my reader the eject-button does nothing. The only way to eject is via the right mouse button.

[http://ubuntuforums.org/showthread.php?p=4799223#post4799223]("http://ubuntuforums.org/showthread.php?p=4799223#post4799223")

---

### Post by Rubadubdub on 2008-04-27
I solved the problem I was having. 

It had to do with my DVD writer using the wrong UDMA. Which had to do with (new) sata driver taking over. Adding **all_generic_ide** to the end of my kernel line in the boot grub solved my problems for now.

Check out what I did and the problems I was having in the following thread:
**_[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=767278]("http://ubuntuforums.org/showthread.php?t=767278")[/COLOR]_**

I hope it helps you to.

---

### Post by LostInBrittany on 2008-05-01
I'm having the same problem, after upgrading both my laptop and my desktop are unable to mount DVDs.

I hope somebody will find an answer soon...

---

### Post by Pumalite on 2008-05-01
Dis you try: all_generic_ide in the boot line?

---

### Post by LostInBrittany on 2008-05-01
Yes I did, I have :
```
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8532c69d-e076-4c7e-85cf-c8387d6783c2 ro quiet splash all_generic_ide
```

---

