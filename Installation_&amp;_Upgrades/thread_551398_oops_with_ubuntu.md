---
title: "oops with ubuntu"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by htdjose on 2007-09-15
im new to ubuntu, and with your guys's help i got it working, it rocks!!, but one thing is when i first installed it(i installed ubuntu twice) i didnt know what was wrong when it wouldnt start up(i guess i needed to put noapic in there) well i did that, but now, when grub comes up, it shows that i have two copies of ubuntu installed on my computer...what can i do?
=swoop=

---

### Post by forestpixie on 2007-09-15
Did you upgrade the kernel (big update download manager) - you've probable got two kernel versions in grub - or are you talking about the recovery mode.

As long as you can start the first line - I suspect all is well

---

### Post by zero-9376 on 2007-09-15
yeah this isn't a problem, ubuntu leaves the old kernels there so that you can boot into the old one if the new one isnt working, there is also the recovery mode which boots into a console with superuser privelliges.
both of these things have saved me on numerous occasions

---

### Post by lisati on 2007-09-15
BTW, for some programmer types, "oops" refers to "Object Oriented Programming System"

---

### Post by htdjose on 2007-09-15
yeah, well i installed it twice(ubuntu) because i thought it wasnt installed right the first time so now i have two kernels, and two recoverys, they both boot, but it just dosent feel right having those two there...can i format the harddrive? and then reinstall ubuntu...???
=swoop=

---

### Post by t3hi3x on 2007-09-15
did you format the harddrive when you installed it the first time?

with linux you can have two kernels installed with the same software configuration. This allows for an easy recovery when a new kernel is rolled out. 

Are the numbers different: (this is an example)

Ubuntu 2.6.20-16
Ubuntu 2.6.20-16 Recover
Ubuntu 2.6.20-15
Ubuntu 2.6.20-15 Recover

If they are then you dont have two versons of ubuntu istalled only two versions of the kernel

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel) tells more about the linux kernel and it will help you understand how it is different from the windows kernel

---

### Post by forestpixie on 2007-09-15
> can i format the harddrive? and then reinstall ubuntu...???indeed you can, if that's what you want to do - just do it once this time :)

if I had time though I'd be inclined to have a bash at working out how to get rid of one of the installs, getting the menu.lst right - nothing to lose if you were going to reinstall anyway

this is my fdisk -l, hda - is referenced as hd0 by the menu.lst, hdb as hd1, partitions follow same logic starting from 0

```

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1094     8787523+  83  Linux
/dev/hda2            1095        9889    70645837+  83  Linux
/dev/hda3            9890       10011      979965   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         829     6658911   83  Linux
/dev/hdb2             830        8358    60476692+  83  Linux
/dev/hdb3            8359        9729    11012557+  83  Linux
```

This is part of my menu.lst
this boots gutsy from hdb3
> title		Ubuntu, kernel 2.6.22-11-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-11-generic
quiet
and this boots feisty from hda1
> 
title		Feisty Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


good luck with it all though

---

### Post by forestpixie on 2007-09-15
you could also run this from a terminal 

```
cat /boot/grub/menu.lst
```

post it here and someone will tell you what you really have

---

### Post by t3hi3x on 2007-09-15
good idea!

---

### Post by gali98 on 2007-09-15
Okay first of all it looks like you updated. as in the update manager. This would give you two kernels (well four including recovery) as there was a kernel update after feisty came out. I would not recomend deleting them at all. as one user said, they will be help later. If your worried about space issue, they're not taking up much space at all. you don't have Ubuntu installed twice.. Trust me. If you reinstalled it took out the last kernels. If it REALLY bothers you, edit /boot/grub/menu.lst and find the place where it lists all the kernels. It'll have a list with  four slightly different lists that look like this... 

title Feisty Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro single
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot

find the titles of the ones you wish to delete and just delete the whole block of stuff. The block being the thing that is above.  Another thing to do is to just not go into the list by pressing ESC when booting so you wouldn't have to see the list. If it automatically does go into the menu edit menu.lst and put "hiddenmenu" after it says "timeout=some #" 
You can also change the time it takes to load the default kernel by changing timeout.
I hope I din't confuse you. I kind of ran around in circles. Basically you really shouldn't delete these kernels. You might need them. Also there is no point in reinstalling since you using the updater will install the kernel again. I hope this helps,
Kory

---

### Post by mocoloco on 2007-09-16
Instead of editing the extra kernels out of the grub menu, why not actually remove the extra kernels?  It also saves a few hundred MB from your hard drive.
Check [this thread]("http://ubuntuforums.org/showthread.php?t=551619") for an easy way to do that.  You can check your current kernel by seeing what's in the grub menu, or from a terminal ```
uname -a
```

---

### Post by htdjose on 2007-09-16
okay thanks you guys, so its the update that gave me the other kernel, okay, thanks you guys
=swoop=

---

### Post by forestpixie on 2007-09-16
glad you're happy - can you mark thread solved if you feel it is (use thread tools) :D

---

