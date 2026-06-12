---
title: "[SOLVED] bootloader installation help"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by rprieto90 on 2008-01-11
i recently installed ubuntu latest release on my windows pc, from a live cd, then after i booted the live cd i installed it from the desktop icon, and all went well during the installation (except the first time when i had to reboot since the pc froze)
then it told me to reboot and take off live cd, i did it, and then the bootloader popped up just as it is supposed to, but when i choose ubuntu, it just goes black and never loads, i waited for about 5 minutes and nothing happen (i don't think i have to be waiting much longer, as nothing happened in that time, and my pc isn't that slow)

---

### Post by meindian523 on 2008-01-11
During the first time,what was the stage of installation when you had to reboot?

---

### Post by rprieto90 on 2008-01-11
i got up to where i had to partition a disk
i formatted d: and then i clicked on new partition or something like that, the option that lets you choose how much space will be asigned for the linux partition, then i just clicked cancel as i didn't wan't the settings and nothing happened, the again and again and again, also the same with ok and i just got nowhere, so i rebooted
should i reinstall it?

---

### Post by meindian523 on 2008-01-12
What do you mean by again and again and again?Do you mean you aborted the installation three times at the partitioning step?

---

### Post by rprieto90 on 2008-01-12
i mean i clicked cancel, nothing happened, then i clicked it again (after some time obviously), and again, clicked it many times and nothing happened, did the same with ok button and X (close) button
no i never aborted the installation, i just closed the window where you are to create a new partition, but it never cloes, i obviously cancelled it when i rebooted, but i didn't cancel it but once

---

### Post by meindian523 on 2008-01-12
I think it would be easier to just reinstall,did you check the CD before installing?

---

### Post by rprieto90 on 2008-01-12
not really, i'll check the cd and then reinstall it
i just boot with live cd and install again?theres no special remove / reinstall procedure?

---

### Post by meindian523 on 2008-01-12
First Check the CD.
The way to uninstall Ubuntu is to delete it's partitions,but since you are just installing again,you can just take your old partitions and mount points and allow the partitions to be reformatted.

---

### Post by rprieto90 on 2008-01-12
ok i checked the cd, it's ok
i'll try what you told ,me, but on mount points, i click the mount points button/arrow and nothing appears, do i have to input it myself? if so what shall i put?

---

### Post by meindian523 on 2008-01-12
Just use what you did earlier,I'm assuming you have two partitions,1 ext3 and 1 swap

Give the mount point for the ext3 partition as /
Swap partitions don't require any mount points.

---

### Post by rprieto90 on 2008-01-12
thanks man i finally got it to work, i figured out i had to partition swap without mount points and i waited a little longer after bootloader, the i saw your post and i knew i had done right
thx

---

### Post by meindian523 on 2008-01-13
cool.please mark the thread solved.

---

