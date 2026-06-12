---
title: "pci=nomsi and fd0 errors"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Fenris_rising on 2008-04-30
hi all just wanted to throw these in. i have just fully installed ubuntu HH. having already tried it through the install in windows method. one of the problems many of us have had is fd0 errors leading to initramfs. also some people have had it where adding the pci=nomsi has failed to get their cd to boot as well. 
as ive said ive just installed fully and 2 things i noticed. (i had problems with fd0 first time around so i disable floppy drives in bios) this time i had a bit of a problem as the floppy disk either failed (needed it to install raid drivers) or the floppy controller went wonkey. so i made a new disk and changed my floppy ribbon cable which was a double (a and b but only one floppy) for a single ended cable. got my raid drivers in and carried on installing HH without disabling the floppy in bios. now the fd0 error didnt happen at all, is the type of ribbon your floppy drive is attached to an issue?? also for those who find nomsi didnt work i made this error. at the end of the line that pops up when you press F6 you get something like 'quiet splash --' what i did when i entered the pci=nomsi argument was this 'quiet splash pci=nomsi--' looks ok doesnt it............it should look like this 'quiet splash pci=nomsi --' note the space at the end between the i and --. i didnt realize i needed the space there and it invalidated the command! dont know if that info is of any use to anyone hope it may help.

regards

fenris

---

