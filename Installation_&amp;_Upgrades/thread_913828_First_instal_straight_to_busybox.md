---
title: "First instal straight to busybox"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by stiiky on 2008-09-08
Hello ubuntu-ers,
I am trying to instal ubuntu and i am getting the same error, regardless of instal from usb, cd, dvd, mounted iso or from in windows.
I initially got the error message (xxx.xxxxxx) which was a series of numbers that increased in size to about 700.000000 followed by "file buffer error I/o fd0 logical block 0" or something similar. This would get to about 700 hundred then go straight to the busy box. I am sure that there have been solutions to this problem posted, just couldn't find the right one for me (all seemed to be for old intalls). If anyone can post a link to a solution, or propose one yourself, i would be most appreciative.
Many thanks,
Stiiky

---

### Post by epidemiks on 2008-09-08
yes, pain in the posterior this one..
as your error message relates to a floppy drive (i think) "fd0", try adding "floppy=off" to the end of the grub menu item in question.. i think its F6 to edit

---

### Post by Partyboi2 on 2008-09-08
Another boot option to try is [FONT=monospace]
[/FONT]```
all_generic_ide
``` As mentioned by epidemiks you would press F6 at the main menu and add it to the end.
Another thing you could try is to disable your floppy in the bios if you are able to.

---

### Post by stiiky on 2008-10-29
thanks for the help there,
only thing is i do not know how to add those to the f6 command. i have disabled floppy in bios and nothing is plugged in that acts as a floppy.bootable.
any other suggestions on trying to get it to load?
many thanks for the help.
Stiiky

---

### Post by Partyboi2 on 2008-10-29
When you boot the ubuntu cd and get to the main menu where you choose to install ubuntu or to check cd for defects or test memory etc press the F6 key then at the end of the line after the last word add the boot option that you are trying, so add either ```
all_generic_ide
``` or ```
nofloppy
``` then press enter to boot.

---

### Post by stiiky on 2008-10-29
Thank you very much. It worked fine now, so i can now get down and dirty with ubuntu. Partyboi2, you rockses!
Thank you for helping me and i hope i can give back to the community when i have gotten to grips with it all.
Stiiky

---

