---
title: "Installing Linux on DoD erased HD"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by zx5itouch on 2008-07-29
Hello Linux fans, I own a Dell 530 Desktop and it seems that I cannot use DBAN to effectively erase the data on my SATA II HD. It stops before it can eve load up the interactive menu with bad sectors message. The Desktop is brand new.
Any suggestions?

Also, I wanted to ask if it is required to make a driver CD that contains all the driver exe files from Dell and choose to perform an OEM Install from any of the Ubuntu/Kubuntu Alternate Install CD's. 

It seems that every time I try to install Ubuntu/Kubuntu or whaterver Ubuntu distro on an erased HD, the install freezes or just doesn't want to boot after removing the install CD.

Any help would be appreciated.

---

### Post by Potatoj316 on 2008-07-29
the alt CD should not be required.  You can try taking out (or unplugging) your HD and then trying to boot the live CD.  If it still does not work then it is not the HD, if it works then it is probably the BIOS trying to boot the erased HD for some reason.  You could also check CD for defects, it sounds like thats a possibility.

Also drivers are not required, even if they were you probably couldnt use windows drivers.

My sugestions:
Check your BIOS boot order, CD should be before HD
Try taking out the HD then booting the CD
Check CD for defects

---

### Post by jimv on 2008-07-29
> **zx5itouch said:**
> Hello Linux fans, I own a Dell 530 Desktop and it seems that I cannot use DBAN to effectively erase the data on my SATA II HD. It stops before it can eve load up the interactive menu with bad sectors message. The Desktop is brand new.
Any suggestions?


Yeah, RMA the drive and get another one.

---

### Post by zx5itouch on 2008-07-29
I like the Ubuntu Studio Linux Distro, which is an Alternative CD which has installed fined in the past. I just received another 160GB HD from a co-worker to swap for testing as well. It just seems that Kubuntu and Ubuntu alternatives/Live CD's haven't worked well yet except for the Ubuntu Studio Alternative. I have tried to run the CD Integrity test, which it tests fine, however, I get the DRDY flashing accross the screen after finishing the Install and re-booting after Kubuntu Load screen hangs forever. I would really like to get DBAN working on this HD & cannot figure out why it won't work, must be Dell's HD choices. It works on all my other Dell machines.

---

### Post by SkonesMickLoud on 2008-07-29
Out of curiosity, where did you get this DoD "erased" HDD?

The DoD does not erase HDD's and then sell them.  DoD policy on broken or unneeded HDD's is literally to take them out back and hit them with a sledgehammer until they're left with tiny pieces.  They then send said pieces off to be incinerated.

The DoD standard mentioned in DBAN is used if they are reusing said HDD within the same agency/department.

---

### Post by Potatoj316 on 2008-07-29
I was wondering that as well.  There really is no way to "erase" a HD. (sure you can shred/format/shred again/write random data, but it is still recoverable)  Perhaps thats your problem.  Maybe they damaged the disk.

---

### Post by zx5itouch on 2008-07-29
I have attemtped to erase my HD shipped with my Dell 530 with Darik's Boot and Nuke CD iso which has worked on many machines but Dell's HD's. I will try to use BCWipePD to erase the HD and try installing Ubuntu Studio Alternative CD or the plain old Ubuntu 8.04.1 LTS Live CD.

[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by Sef on 2008-07-29
> I was wondering that as well. There really is no way to "erase" a HD. (sure you can shred/format/shred again/write random data, but it is still recoverable)

If you overwrite it enough, the data is nearly impossible to recover.

---

### Post by SkonesMickLoud on 2008-07-29
> **zx5itouch said:**
> I have attemtped to erase my HD shipped with my Dell 530 with Darik's Boot and Nuke CD iso which has worked on many machines but Dell's HD's. I will try to use BCWipePD to erase the HD and try installing Ubuntu Studio Alternative CD or the plain old Ubuntu 8.04.1 LTS Live CD.

[http://www.dban.org/download](http://www.dban.org/download)

Ooh, I read your post wrong.  I thought you somehow got a hold of an old DoD HDD.  Not something a smart person would boast about over the interwebs.

If you're just trying to wipe your disk and start over, you can use the "Binary" (I forget what it's actually called) method of deletion, which simply over writes 10101010101010 across your whole disk.  This way took ~45 minutes on my 250GiB.  The DoD method is waaaaay more than you need.  The largest drive I've used it on was 500 GiB, and took 11 hours.

---

### Post by Potatoj316 on 2008-07-30
> **Sef said:**
> If you overwrite it enough, the data is nearly impossible to recover.

Note the nearly impossible.  It is still (theoretically) possible to recover after 25 rewrites.

---

### Post by zx5itouch on 2008-07-31
I was able to use BCWipePD which allows you to customize an iso to create a bootable CD-ROM to wipe HD clean. DBAN 1.07 and 2.0 do not work on Duo Core processors. The only version of Ubuntu I have had successful installation with is Ubuntu Studio wich uses the rt kernel. I do believe there is a problem installing any flavor from Ubuntu. The problem is the installation completing then rebooting the system only to give out DRDY errors. This flaw is not found in the Ubuntu Studio release.

---

