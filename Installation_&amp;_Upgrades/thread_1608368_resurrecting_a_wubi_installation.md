---
title: "resurrecting a wubi installation"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by glennharm on 2010-10-28
[FONT=Arial]Hi,[/FONT]
 
[FONT=Arial]I had ubuntu running in wubi just fine for several weeks. [/FONT]
 
[FONT=Arial]I had to do some system reconfiguration which forced me to re-initialize the whole drive that wubi was installed in. [/FONT]
 
[FONT=Arial]I saved the whole \ubuntu directory thinking I could just re-install wubi, rename the new ubuntu directory, copy in the old ubuntu directory in it's place and life would be good. [/FONT]
 
[FONT=Arial]Not so. [/FONT]
 
[FONT=Arial]I found an article which seemed to cover this sort of scenario so I tried the following: [/FONT]
[FONT=Arial]- Installed wubi[/FONT]
[FONT=Arial]- Made sure it booted[/FONT]
[FONT=Arial]- Didn't complete the installation--rebooted to windows[/FONT]
[FONT=Arial]- Replaced just the root.disk file from the old installation, overwriting the newly created root.disk file.[/FONT]
[FONT=Arial]- Booted wubi[/FONT]
[FONT=Arial]- I get the grub menu, then after that I get the following error message:[/FONT]
 
 
[FONT=Arial][FONT=arial]```
[FONT=arial]error: no such device: 3d2ad2c672a636db.[/FONT]
[FONT=Arial]error: file not found.[/FONT]
[FONT=Arial]ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell![/FONT]
 
[FONT=Arial]BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)[/FONT]
[FONT=Arial]enter 'help' for a list of built-in commands.[/FONT]
(initramfs)
 

```
 
[/FONT]
Any thoughts on how I can resurrect my existing wubi installation?
[/FONT]
 
Thanks!

---

### Post by bcbc on 2010-10-29
when you see the grub menu, hit 'e'. Delete the line with the search command - it refers to a uuid on the old partition. Then hit CTRL+X to boot.

As long as the ubuntu folder is on the same partition, it should boot. If you changed the partition when you reformatted, then you'll need to figure out which one and change it (i.e. references to (hd0,2) or (hd0,msdos2) and /dev/sda2).

I've moved Ubuntu the root.disk around a lot - you can boot it direct from a grub prompt provided you know where it is (which partition). So it's likely just a little effort to get it to work. Once booted, run "sudo update-grub" to regenerate the grub menu.

---

### Post by glennharm on 2010-10-29
Thanks much, bcbc!
 
Worked like a champ!
 
I did notice one oddity that I don't believe I saw before and that is about a 3-4 second lag between when I hit enter on the boot entry and when I can actually see ubuntu starting.

---

### Post by megatronous on 2010-12-14
alll thought the above problem solved my issue now ....when i booted my pc again after this solution......my screen had gone blank ....and i am not even able to see bios page....in the start ...the monitior just stays blank..................i have even tried disconnectiong my hard disk but still not able to get the display......solution required ....urgently.....

---

### Post by oldfred on 2010-12-14
Did you install grub to the MBR. You still need to boot windows with wubi as it uses windows to boot first then loads grub.

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by megatronous on 2010-12-15
thanks for the reply.......neways but i found tht my monitor is blown......pc is working on other monitor..

---

