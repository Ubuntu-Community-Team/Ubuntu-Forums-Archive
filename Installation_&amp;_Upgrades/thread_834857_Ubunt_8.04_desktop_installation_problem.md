---
title: "Ubunt 8.04 desktop installation problem"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by sneffers on 2008-06-19
Ok, I'm slightly new to ubuntu/linux. I have used it in year's past and had a few problems but I switched back to windows for certain reasons but I really miss ubuntu. I have a dell inspiron 530. I tried using my old ubuntu 6.04 cd to install ubunt and upgrade from there but that didn't work and idk why. I decided to burn a new cd with the latest version 8.4. I installed it right inside windows as a dual boot. when I restarted the computer it stayed on teh graphical loading screen for a minute or 2 and then it went to some error and this is what I have of it:

[ 203.716599] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[ "more numbers"] ata2.00: cmd a 0/00:00:00:24:00/00:00:00:00:00:/a0 tag 0 pi 36 in

[ "numbers"] ata2.00: satus: {dry}

and that's all I remember there was one little thing before that but I forgot what that was. I hope you can help me and thanks for your time.

---

### Post by sneffers on 2008-06-26
I really want help with this!

---

### Post by oldos2er on 2008-06-26
Did you run 'Check CD for defects' on the 8.04 cd?

---

### Post by david_9933515 on 2008-06-26
> **oldos2er said:**
> Did you run 'Check CD for defects' on the 8.04 cd?

I've encountered this problem before.  It priolly has nothing to do with the CD, but check it nonetheless.  Try going into your BIOS and setting your system to use RAID.  This solved the installation problem for me.

But, afterwards, it really screwed up my system when it came to booting.  Switching it back to IDE only allowed me to boot into WinXP.  I really had trouble accessing CD's, burning/copying CD/DVD's.  Can anyone chime in and let me know what the problem is?

---

### Post by sneffers on 2008-07-08
I tried checking the cd for defects but it started loading ubuntu and I got the same busybox error thing.

---

### Post by Pumalite on 2008-07-08
Do md5sum on the iso first, then check CD integrity, Burn at 4x or less. Do not use CD-RW. Clean the lens in your burner.

---

### Post by sneffers on 2008-07-08
I did burn at the lowest speed. I don't know about computers so I don't know how to clean the lens in my burner and I didn't use CD-RW (at least I don't think so).
P.S. I tried changing to RAID in the bios but that just messed up vista so I really hate my computer right now

---

### Post by Pumalite on 2008-07-08
You can try the Alternate CD or; if you are the adventurous type; try some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_gener4ic_ide vga=0x317 vga=788 vga=789 vga=791
To be tried alone or in different combinations until you hit the right one.

---

### Post by sneffers on 2008-07-08
That whole last comment seemed like a dif. language I'm sorry but I didn't read the website that could be why =D. I just changed the boot thing to raid again and I got to run ubuntu off the live cd (8.04 is amazing by the way) and now I am installing it inside windows so I have just one partition and I will see if it will let me boot it in ubuntu. thanks for all your help so far, I'll reply again if It doesn't work =D

---

### Post by sneffers on 2008-07-09
I tried installing it but it didn't have the option to boot in ubuntu so I uninstalled it and now I am trying to install it from the live cd but it won't work because it won't let me partition the disk.....

---

### Post by Pumalite on 2008-07-09
Get Gparted Live CD and partition ahead of time:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
If nothing works; try the Alternate CD.

---

### Post by sneffers on 2008-07-10
Well I had ordered a cd a couple weeks ago and it came yesterday and I booted it up with the live cd and would'nt you know it, it installed without any problems. but there is still a few stranget things if you would be willing to read further:
I have two users, the one I created when installing works perfectly fine no problems, the other user won't allow visual effects and games run really slow, my graphics card is pretty decent and I think it has something to do with the user since all these things work fine on the first user account.

---

