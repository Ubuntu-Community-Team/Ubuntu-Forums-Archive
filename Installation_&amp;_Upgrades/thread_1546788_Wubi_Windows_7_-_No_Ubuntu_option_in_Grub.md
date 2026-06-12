---
title: "Wubi Windows 7 - No Ubuntu option in Grub?"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by nightfire117 on 2010-08-05
Hey all. I'm aware that Wubi doesn't install Grub. The normal Windows 7 bootloader comes up and I am given two options: Windows 7 or Ubuntu.

So here's what happened:

I installed Ubuntu 10.04 through Wubi on my laptop (not my desktop which has had 10.04 on it before). I haven't used Wubi before, but anyway... after I installed it I rebooted and selected Ubuntu. Ubuntu loaded whatever it had to in order to prepare the system and went to reboot.

After the system rebooted I selected "Ubuntu" again. Of course the setup for Ubuntu was done so I didn't go back into that. Instead I'm presented with a Grub menu. But the only options are "Windows Vista" and "Windows 7" (Vista being the recovery install that came with the laptop, and I upgraded to Windows 7).

So basically there's 3 partitions (excluding Ubuntu if Wubi makes partitions): 1. Vista recovery 2. Windows 7 (~150 GB) 3. Media/whatever partition (~150 GB)

So why's there no Ubuntu option there?! I don't know how to add Ubuntu so Grub sees it - because does Wubi actually create another partition... or how does this work? It should work by default. :(

(Yeah I know there's a lot of topics that have similar titles, but their issues are slightly different - as such I haven't pieced anything together. Adding Windows to GRUB is a lot easier than the other way around and adding Ubuntu to GRUB. >_>)

~Night

---

### Post by bcbc on 2010-08-05
> **nightfire117 said:**
> Hey all. I'm aware that Wubi doesn't install Grub. The normal Windows 7 bootloader comes up and I am given two options: Windows 7 or Ubuntu.

So here's what happened:

I installed Ubuntu 10.04 through Wubi on my laptop (not my desktop which has had 10.04 on it before). I haven't used Wubi before, but anyway... after I installed it I rebooted and selected Ubuntu. Ubuntu loaded whatever it had to in order to prepare the system and went to reboot.

After the system rebooted I selected "Ubuntu" again. Of course the setup for Ubuntu was done so I didn't go back into that. Instead I'm presented with a Grub menu. But the only options are "Windows Vista" and "Windows 7" (Vista being the recovery install that came with the laptop, and I upgraded to Windows 7).

So basically there's 3 partitions (excluding Ubuntu if Wubi makes partitions): 1. Vista recovery 2. Windows 7 (~150 GB) 3. Media/whatever partition (~150 GB)

So why's there no Ubuntu option there?! I don't know how to add Ubuntu so Grub sees it - because does Wubi actually create another partition... or how does this work? It should work by default. :(

(Yeah I know there's a lot of topics that have similar titles, but their issues are slightly different - as such I haven't pieced anything together. Adding Windows to GRUB is a lot easier than the other way around and adding Ubuntu to GRUB. >_>)

~Night

This is kind of weird... since the grub menu you are seeing comes from the root.disk you installed with wubi (no partition, this is a virtual disk), yet it doesn't have ubuntu, only windows.

I'd try reinstalling - no idea why this happened, or if it will happen again.

---

### Post by nightfire117 on 2010-08-05
That's the thing - I've reinstalled it once already, and no difference. :???: Thanks for the clarification about the virtual disk thing.

[Edit]: Keeping in mind your comment that Grub shouldn't be installed by Wubi ([here](http://ubuntuforums.org/showthread.php?t=1546603)), *should* I install GRUB, just to see what would happen? I can always remove it by doing the fixmbr from the Windows command prompt (recovery disk).

**[Edit 2]:** I decided to try and pay closer attention this time around and a message flashed by saying 'no WUBILDR' or something along those lines and something about hd(x,x) (didn't catch the numbers). What could this be? Obviously the WUBI loader, but... is that why it's not seeing the Ubuntu virtual drive?

---

### Post by bcbc on 2010-08-05
> **nightfire117 said:**
> That's the thing - I've reinstalled it once already, and no difference. :???: Thanks for the clarification about the virtual disk thing.

[Edit]: Keeping in mind your comment that Grub shouldn't be installed by Wubi ([here](http://ubuntuforums.org/showthread.php?t=1546603)), *should* I install GRUB, just to see what would happen? I can always remove it by doing the fixmbr from the Windows command prompt (recovery disk).

**[Edit 2]:** I decided to try and pay closer attention this time around and a message flashed by saying 'no WUBILDR' or something along those lines and something about hd(x,x) (didn't catch the numbers). What could this be? Obviously the WUBI loader, but... is that why it's not seeing the Ubuntu virtual drive?

Don't install the grub bootloader. It won't work. You are using grub4dos (wubildr) within windows, and it is reading your virtual disk already - that's not the issue - just you don't have ubuntu in the menu.

I don't think the no WUBILDR is an issue. It is finding the virtual disk.

If you can boot a live cd then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Not sure whether this will do much good - I've never seen this problem before. But if you feel like playing with it.

---

### Post by Loki_Trickster on 2010-08-08
> **nightfire117 said:**
> Hey all. I'm aware that Wubi doesn't install Grub. The normal Windows 7 bootloader comes up and I am given two options: Windows 7 or Ubuntu.

So here's what happened:

I installed Ubuntu 10.04 through Wubi on my laptop (not my desktop which has had 10.04 on it before). I haven't used Wubi before, but anyway... after I installed it I rebooted and selected Ubuntu. Ubuntu loaded whatever it had to in order to prepare the system and went to reboot.

After the system rebooted I selected "Ubuntu" again. Of course the setup for Ubuntu was done so I didn't go back into that. Instead I'm presented with a Grub menu. But the only options are "Windows Vista" and "Windows 7" (Vista being the recovery install that came with the laptop, and I upgraded to Windows 7).

So basically there's 3 partitions (excluding Ubuntu if Wubi makes partitions): 1. Vista recovery 2. Windows 7 (~150 GB) 3. Media/whatever partition (~150 GB)

So why's there no Ubuntu option there?! I don't know how to add Ubuntu so Grub sees it - because does Wubi actually create another partition... or how does this work? It should work by default. :(

(Yeah I know there's a lot of topics that have similar titles, but their issues are slightly different - as such I haven't pieced anything together. Adding Windows to GRUB is a lot easier than the other way around and adding Ubuntu to GRUB. >_>)

~Night



I installed ubuntu with wubi in my lappy and facing same problem as you. No boot option for ubuntu although installation went without errors. Still finding solution for it. please let me know if you find how to correct this problem.

---

### Post by bcbc on 2010-08-08
I saw another thread where it looked like the person had booted from the grub command prompt (wasn't clear). 

You can try this: when you see the grub menu hit 'c' to get to the command prompt. Then enter:
ls (small LS to see what partitions you have e.g. (hd0,1), (hd0,2)

Find your root.disk (try each partition until you find it)
ls (hd0,1)/ubuntu/disks/root.disk

Assuming you find it on (hd0,1) then you'd use /dev/sda1.. (hd0,5) = /dev/sda5 and (hd1,2) = /dev/sdb2 (substitute these in the following manual boot commands):

```
insmod ntfs
set root=**(hd0,1)**
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=**/dev/sda1** loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

If it works, then try and update the grub menu and see if it picks up the ubuntu kernel:
```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-08-08
Wubi should be in Windows 7 bootmanager: bcdedit

At command line in Windows 7 with administrative permissions:

```
bcdedit
```Should be a wubildr or something close in one of the entrys in bcdedit

The Vista is just the way linux reads the Windows 7 recovery partition. 

WUBI will be in Windows C: drive right next to Users. Also a uninstall there.
Make sure after you uninstall and always through Wubi and not ADD and REMOVE
programs in Windows. Will sometimes leave the wubibldr in bcdedit if not done in the
wubi uninstall. Anyway make sure after uninstall the wubildr is gone in bcdedit. Then reinstall. Takes very little time to unintall and reinstall
Also check launchpad for any bug notices.

---

### Post by bcbc on 2010-08-20
FYI I've found out that this problem is caused by clicking the SKIP button during the installation. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028)

If this is what happened, the solution is to let the installation finish uninterrupted.

---

