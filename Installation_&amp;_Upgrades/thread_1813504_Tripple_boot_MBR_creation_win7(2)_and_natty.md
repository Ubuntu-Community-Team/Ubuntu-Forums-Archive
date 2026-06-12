---
title: "Tripple boot MBR creation win7(2) and natty"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by inertself on 2011-07-27
I have a setup with 3 hard drives.  The first hard drive has windows 7 and is a solid state, for my fast computing needs.  The second hard drive has another copy of windows 7 on one partition and Ubuntu 11.04 on another (and SWAP space).  The third hard drive is just storage.  Grub is installed on the first(SSD) hard drive, as well as the MBR (master boot record) for the two windows installs (select win7 in grub, then it lets me select which windows install to boot).  Now I want to get rid of my solid state drive, and just run from the second hard drive with dual boot.  How can I install a new MBR on the second hard drive without having to re-install both OS's?  I've tried removing the first hard drive and using bootrec.exe to re-write the MBR and it will not work.  I can install grub, and it boots to ubuntu but when I try windows 7 it says there is no MBR.  Any suggestions?

---

### Post by YesWeCan on 2011-07-27
Hi there.
Your second W7 may be relying on boot files on the SSD. You might try disconnecting the ssd and then repairing the W7 on the second disk using your W7 CD. afterwards youll need to reinstall grub and update it.

Tip: as you have a third HD, why not install grub to its mbr so that the disk with W7 retains the Windows mbr code. Set the bios to boot off the third disk. This can avoid problems in the future if W repairs the mbr.

---

### Post by inertself on 2011-07-27
Yes my second windows 7 is relying on the SSD's boot record, I've tried disconnecting it and fixing it with bootrec.exe, and it doesn't write anything.  I'll try again and see if it works this time.  I don't want to use my storage drive because I remove it from time to time and use it between computers, although I didn't think of that.  Thanks for helping :)

---

### Post by inertself on 2011-07-27
OK so the bootrec.exe keeps saying "element not found".  I guess it's looking for an existing MBR to rewrite, and cannot find it.  How do I go about writing a new MBR??  is there a way to copy it from my SSD?

---

### Post by YesWeCan on 2011-07-27
Are you using a windows CD for this? It ought to be able to find your W7 and repair the mbr. Im not familiar with it.
You might check the W7 partition is active ( boot flag set). Use sfdisk to set it if not.
You can copy the mbr boot code (do not copy the partition table!) over from the ssd using dd. It is rather risky if you are not familiar with dd and youll have to reinstall grub if it doesnt work. Dont do this unless you know what you are doing.
sudo dd if=/dev/sdb bs=512 count=1 > mbrbackup
sudo dd if=/dev/sda bs=446 count=1 of=/dev/sdb

---

### Post by inertself on 2011-07-27
OK, maybe it is the boot flag.  Yes I am using a windows 7 cd in the command prompt.  It can recognize c:/windows when I do bootrec.exe /ScanOs, and also when I do /RebuildBcd, but when I select Yes to write it, it says element not found.  

I changed the boot flag using gparted, I'll see if that works.

---

### Post by YesWeCan on 2011-07-27
I think bootrec has a fixmbr option

---

### Post by inertself on 2011-07-27
OK - so the windows CD recognizes the windows install right off the bat.  Only problem now is that it is not the correct version?  I guess since it wasn't installed from that cd then it will not fix it?  looking for other options at this point.  I think there is a way to do it from ubuntu live cd, I've only seen old posts about it though and not sure if my 11.04 will do it.

---

### Post by inertself on 2011-07-27
OK, I just had a big duh, I made a system repair cd within the windows installation I wanted to fix, and then used that to automatically repair my MBR.  worked like a charm.  Thanks for your help YesWeCan :)

---

### Post by inertself on 2011-07-27
OK so I re-installed grub and it was pointing to the SSD to start windows, so all I had to do was edit the grub.cfg file, correcting the windows 7 uuid (I think that is what it is), 66764F........  anyway all is well, now I just need to figure out how to make the SSD drive work again :)  Basically moving the MBR to my 2nd hard drive I guess.

---

### Post by YesWeCan on 2011-07-28
> **inertself said:**
> OK so I re-installed grub and it was pointing to the SSD to start windows, so all I had to do was edit the grub.cfg file, correcting the windows 7 uuid (I think that is what it is), 66764F........
If you are using Grub2 you don't need to edit grub.cfg. You just need to run 'sudo update-grub' and it will sniff out your OS's and add them to your boot menu correctly. 
> anyway all is well, now I just need to figure out how to make the SSD drive work again :)  Basically moving the MBR to my 2nd hard drive I guess.What do you mean by "moving my MBR to the 2nd HD"? Every disk has an MBR. So you cant move it. You could copy it, but why do you think you need to? I wouldn't touch your Windows/Ubuntu HD now it is working.

---

### Post by Mark Phelps on 2011-07-28
> **inertself said:**
> OK so I re-installed grub and it was pointing to the SSD to start windows, so all I had to do was edit the grub.cfg file, correcting the windows 7 uuid (I think that is what it is), 66764F........  anyway all is well, now ...

Unfortunately, if you really DID hand-edit grub.cfg, all is NOT well now ....

There are lines in that file telling you NOT to edit it. Why? Because the next kernel update you do will automatically run update-grub -- and wipe out all the changes you made.

You should either edit /etc/default/grub file (for defaults) or the runtime scripts -- NOT the grub.cfg file.

---

