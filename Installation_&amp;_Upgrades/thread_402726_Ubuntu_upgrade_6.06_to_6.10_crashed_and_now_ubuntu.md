---
title: "Ubuntu upgrade 6.06 to 6.10 crashed and now ubuntu does not boot"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by xen27 on 2007-04-06
Help needed, 

Yesterday i started to upgrade my ubuntu 6.06 to 6.10. everything went well until about 80% of the files were installed. the upgrade application crashed! i noticed some changes on the desktop after this (i.e.some icons had changed). after te crash i couldn't continue it and i had to reboot.

the crash happended while it asked me to keep or overide some file under /etc. (if i remember right it was a file starting with sys***. i didn't have time to select as keep/overide as the upgrade application crashed :(


after reboot the loading of ubuntu stops after:
**"Uncompressing Linux... Ok, booting the kernel."**

selecting any other kernel version doesn't help. the result is the same.

if i start it with "recovery mode" the last info on the screen is:
"
Begin: Running /scripts/init-bottom ...
Done.
[17179577.896000]usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179578.472000]usb 1-2: new low speed USB device using uhci_hcd and address 5
" 
....and this is the place it freezes

the same is without my USB keyboard and mouse (naturally without USB info)

1) how could i get more info about the boot? some way to have "debug" mode on to see what stops the booting process?

2) live cd boots fine, any way i could "recover" the 6.06 stuff (or 6.10) with it? without losing all the info on the harddrive?

3) what log files might be helpful for checking out the problem?

any help appreciated!

---

### Post by lynxus on 2007-04-06
Wouldnt a re-install on the same partitions with NO format bring everything back ? IE: install teh same stuff but shouldnt overwite any data you may already have ?

---

### Post by xen27 on 2007-04-06
so the installation using live cd is possible to do without formatting? i will give it a go.

---

### Post by xen27 on 2007-04-06
well, noticed that i only have /swap and / partitions. so the reinstall would require reformating of "/swap" and "/". = would lose all data :(
i guess there's no other way to do this. so my solution is to go and buy a new HD tomorrow, and install ubuntu from scratch to it. then take all data from the other drive (i.e. configuration info, mysql data..).

---

### Post by datayoung on 2007-04-06
If you not get new HD yet here my solutions why I got same problem as you
I reboot with CD and install new but RESIZE
My HD size 70 G and luckily After Resize I got about 1.5 G
then
I got hda3 instead of hda1
I install and mount the hda1 into data by
mkdir /data
mount /dev/hda1 /data
Now I got all data back 
Lazy again,I want only home from old HD
I rm /home
and ln -s /data/home/ /home
now I got /home back 

if you like all user back It is also no problem to take
cp /data/etc/shadow /etc
cp /data/etc/group /etc/

the mount data and link to home you can play with fstab

Hope can help you on time

---

