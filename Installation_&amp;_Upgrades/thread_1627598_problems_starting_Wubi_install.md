---
title: "problems starting Wubi install"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by dekinstoke on 2010-11-21
Having the same issue with 10.10 and 10.04, that is I am getting the "root disk cannot be found. dropping to shell. initrams"

If I go to recovery mode, hit E and edit the boot script by changing root=(hd1,1) to root=(hd0,1) i can get a text based login and then run startx and it all boots ok.

I have noticed an interesting thing. If I run the disk utility I find that both the IDE hard drives on my system are seen as SCSI/SATA drives, i.e they are given the designations sdb and sdc. Now surely IDE drives should be Hdb and Hdc?

Could this be why the boot is getting messed up? After all if the system is looking for SATA drives which don't exist?

Any ideas would be welcome as it would be nice to have a system that boots first time .....

---

### Post by bcbc on 2010-11-21
All drive designations in Ubuntu are now /dev/sdX

It seems that there was something plugged in or some reason why the drive containing ubuntu was designated (hd1) or /dev/sdb, whereas now it is (hd0) or /dev/sda. So just do the workaround to boot and run "sudo update-grub" and it should correct itself.

---

### Post by dekinstoke on 2010-11-22
I have run sudo update-grub ad infinitum ...still the same issue.

I have learned that there seems to be some issues with the newer kernels and systems with a mix of SATA and IDE drives, depending on whether the system BIOS looks at SATA drives first or IDE.

Also .... if I end up at the initramfs> prompt, cd to Host and then do ls, the contents of the supposed Host drive show it to be the solitary SATA drive on the system .... NOT the first IDE drive where the WUBI "Ubuntu" folder is. Which explains why the system can;t find the root.disk ....it is looking on the wrong drive.

There must be a workaround for this surely? I am considering pulling the 1 x SATA drive out of the PC and going to only IDE to see if that sorts everything out.

---

### Post by dekinstoke on 2010-11-22
Ok.

I removed the SATA drive and the 2nd IDE drive .... reinstalled the WUBI install and now it boots perfectly.

I think the issue is the motherboard I am using, which is an old AMD Athlon64 board and the way the BIOS insists on recognizing any SATA drives before the IDE drives.

I will try an older build of Ubuntu at some point, say 8.04, with all the drives attached and see if that has any issues. If not then it is definately the new "no hdx schema" that Linux has adpoted. Bit annoying, but then I will use 6 year old hardware with a new OS lol --- running 10.10 now btw.

Happy for now :-)

---

