---
title: "new video card, can not install 10.04"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by arnasd on 2010-07-06
Hello,

i'm getting desperate on this one:
recently i installed new video card to my pc (msi nx7600gt) and my pc did not boot - i had error
```
EXT4-fs (device sda1): ext4_lookup: deleted inode reference
```
i started disc check, but during check i got "init: ureadahead main process (226) terminated with status 5". long story short - my HDD got formated and now i can not install lucid 10.04.
with quiet and splash modes removed i got following errors:

```
setting dpms mode 0 on vga encoder
output vga-1 is running on CRTC0 using output C
GPU lockup - switching to software fbcon
console: switching to colour frame buffer device 200x75
```

after that i get:
```
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system
```

my motherboard has integrated videocard, i enabled AGP port on BIOS and my agp card is loaded. i have no installation problems with integrated card, so i assume this problem is caused by my new agp card.

my question is: how to install kubuntu 10.04 32bit with my video new card?
i have several installation cd's, they all are burned on slow speeds (~12x), checked, md5sum correct etc. so problem is in my hardware.

any suggestions on this problem?

thanks,

arnas

---

### Post by WinRiddance on 2010-07-06
If you have an older motherboard sometimes enabling the AGP in the bios isn't good enough since this only opens the door to use your AGP card. On some of the older motherboards you also have to disable the built in graphic chip in order to avoid conflicts. Often this is done by removing a little plastic jumper (or adding one) near the graphic chip on the board. Your manual would indicate what you need to do and if you don't have that try googling your exact mainboard (commonly large text on the edge of the board somewhere). You might get lucky and find some posted specs that could help you.

---

### Post by arnasd on 2010-07-07
i have tried 3 different cd's and 3 different cd drives - i get the same problem, so they are not the issue.
i tried launching installer with parameters "nomodeset", "i915.modeset=0 xforcevesa", "i915.modeset=1" - but it did not help.

also tried 9.10 installation from USB pen drive (i was using UNetbootin), but i got the same error "(initramfs) Unable to find a medium containing a live file system"

my MB is P4i65GV with bios 1.80. it can not disable the integrated video card, it just sets higher priority for VGA card.

so, i'm getting desperate on this :-|

edit:
i found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454158](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454158)
but suggested method did not help.

---

### Post by gradinaruvasile on 2010-07-07
Now that is strange...
A video card should not interfere with the filesystems. Should have been an unclean reset or something. How did the HDD got formatted anyway??? Maybe the file system kicked the bucket, but formatted...?

Stupid question: where is the monitor connected? Make sure you connect it to the add-
on card.

But first remove the nvidia card, connect the monitor to the onboard and boot - see if it works - if works, there is a problem with the AGP card or its setup/handling in BIOS. Check the BIOS options thoroughly.

Use a 9.10 cd for debugging (unetbootin doesnt always work well with ubuntu cds). Also pay attention to the kernel options - if you use the nvidia card, you should force the vesa driver with xforcevesa and disable kms with nomodeset:

"nomodeset xforcevesa" or something for kernel options.

PS: If you reinstall Ubuntu, make sure you use EXT3 for file system.

---

### Post by arnasd on 2010-07-07
thanks for the answer, i just found another person with similar problem as mine:
[http://ubuntuforums.org/showthread.php?t=1515389](http://ubuntuforums.org/showthread.php?t=1515389)

> How did the HDD got formatted anyway??? Maybe the file system kicked the bucket, but formatted...?
hard drive was formatted while installing win xp.

> where is the monitor connected? Make sure you connect it to the add-on card.
monitor is connected to new AGP/VGA card.

> But first remove the nvidia card, connect the monitor to the onboard and boot - see if it works - if works, there is a problem with the AGP card or its setup/handling in BIOS. Check the BIOS options thoroughly.
i can (and i did) install ubuntu/kubuntu 8.10, 9.10, 10.10 on that machine with video card removed.

> PS: If you reinstall Ubuntu, make sure you use EXT3 for file system. 
previously with the last successful installation i was using ext4, it did not make any difference (as i observed).

---

### Post by dino99 on 2010-07-07
not the best idea: *** hard drive was formatted while installing win xp. ***

use the linux tools with ubuntu, like partedmagic to format your partitions

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by arnasd on 2010-07-07
i don't think that formatted hdd is the main reason - if i take my video card out, it works just fine.

i have tried using "nomodeset xforcevesa" arguments, but still i got the same error.

my bios has only one setting that is related to video card:
chipset configuration -> Init. graphic adapter priority
there are three settings:
AGI/PCI/Onboard
Onboard/AGI/PCI
PCI/AGI/Onboard

i am using AGI/PCI/Onboard, but it just sets priority. i have tried all but no impact.

edit: current bios version is 1.80, the latest is 2.30, but it needs floppy disc to upgrade (which i don't have)

---

### Post by arnasd on 2010-07-07
just tried to use live cd and live usb, but still got the same error. i'm running out of ideas...

---

### Post by arnasd on 2010-07-18
i have tried several videocards - Geforce FX5900XT, NX7600GT, some old nvidia 400 and 440mx's. same error whatsoever.
tried almost all possible installation parameters.

when i get (initramfs) Unable to find a medium containing a live file system, i press "enter" and in console i can see all listed directories. /cdrom/ is empty, so i do "mount /dev/scd0 /cdrom" and ls /cdrom dipslays mounted files. after mounting i type "exit" and it continues loading until it again shows error and again i'm at initramfs console. /cdrom is empty again, so i mount /dev/scd0 to /cdrom once more. after exiting console setup stops loading and displays that setup can not find files from /root/.

i think that setup is not compatible with my hardware, and it can not mount cdrom automatically (maybe device name in /dev/ changes after video card installation?), so setup files can not be found and further installation halts.

any suggestions?

edit:
[http://ubuntuforums.org/showthread.php?t=1332782](http://ubuntuforums.org/showthread.php?t=1332782)
seems that i'm not the only one that gets this error.

how can i get syslog from installation setup output?

---

