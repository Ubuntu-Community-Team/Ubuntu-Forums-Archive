---
title: "Strange but big dual boot problem"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by mcarrigan on 2010-05-17
I don't know what I have done, if i did my volumes wrong or what, but here I go...I shrank my Win7 partion to 75GB created another 75GB vol and made it root and installed Ubuntu 10.4 there.  Now here is the problem, after the reboot from the install, loaded Ubuntu just fine.  Did a restart into Win7 to check and that was fine...THEN rebooted to go back to Ubuntu Grub never loaded, it never gave me the option to pick an OS, just sat there at a curser.  So I reloaded Ubuntu, just deleted the Vol that I installed it in before and went through the whole thing.  This time after the reboot went into Ubuntu just fine again. then I rebooted again and the loader came up fine so I went back into Ubuntu this time.  Then I rebooted again back to Win7, BUT when I rebooted again, no Grub.  This time  just as one last check, reloaded again and rebooted and shutdown multi times and as long as I only went into Ubuntu it is fine but as soon as I go to Win7 and restart, I lose Grub...??????

---

### Post by darkod on 2010-05-17
Do you have HP or Dell?

---

### Post by mcarrigan on 2010-05-17
Dell studio 15, brand new

---

### Post by darkod on 2010-05-17
I think you have been hit by this:
[http://ubuntuforums.org/showthread.php?t=1475646](http://ubuntuforums.org/showthread.php?t=1475646)

The last post by oldfred has few links to read.

---

### Post by mcarrigan on 2010-05-17
Ok, so i followed the instruction here in:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
Solution #2 so I could put an older version of grub and see if that works.  I'm having a problem entering the correct info to get Windows to load.  This is what I have in grub:

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		a3446b99-c3d8-4b71-abf7-94b463170523
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=a3446b99-c3d8-4b71-abf7-94b463170523 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		a3446b99-c3d8-4b71-abf7-94b463170523
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=a3446b99-c3d8-4b71-abf7-94b463170523 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		a3446b99-c3d8-4b71-abf7-94b463170523
kernel		/boot/memtest86+.bin
quiet

title		Windows 7
root		(hdY,Z)
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

And when I try to load Windows it says it cannot be found (sorry forgot actual wording). Windows is located on hd3.

Thanks for the help!

---

### Post by darkod on 2010-05-18
> **mcarrigan said:**
> Ok, so i followed the instruction here in:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
Solution #2 so I could put an older version of grub and see if that works.  I'm having a problem entering the correct info to get Windows to load.  This is what I have in grub:

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        a3446b99-c3d8-4b71-abf7-94b463170523
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=a3446b99-c3d8-4b71-abf7-94b463170523 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        a3446b99-c3d8-4b71-abf7-94b463170523
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=a3446b99-c3d8-4b71-abf7-94b463170523 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        a3446b99-c3d8-4b71-abf7-94b463170523
kernel        /boot/memtest86+.bin
quiet

title        Windows 7
root        (hdY,Z)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1

And when I try to load Windows it says it cannot be found (sorry forgot actual wording). Windows is located on hd3.

Thanks for the help!

Sometimes you need in the windows entry the command:

makeactive

only I don't remember whether before the map commands or before chainloader.

Also, you could post the results of the boot info script which will show us more. Instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by mcarrigan on 2010-05-18
Still didn't work, here is the actual message:

Error 23: error while parsing number

Press any key to continue...

---

### Post by oldfred on 2010-05-18
What partition is your windows in 
root        (hdY,Z)

and for window 7 rootnoverify often works better than just root.
rootnoverify (hdX,0)

Y is the drive  and Z is the partition. In old grub partition count starts at 0 so sdd1 will be (hd3,0). sdd2 (hd3,1) etc.
Both grub and grub2 count drives from 0.

Post the boot_info script if you need more help.

If by third drive you mean sdc then it is (hd2,0) etc

---

### Post by mcarrigan on 2010-05-20
Well, I appreciate the help with trying to get Windows mapped back into the grub boot list but I was still not getting it so I backed up and went a different rout.  I still needed to fix an un-allocated disk space issue so i reloaded Ubuntu again then went to Windows and stopped the programs that were righting to the MBR and all works now...now my unallocated space issue, huh...but that's for another post.  Thanks

---

