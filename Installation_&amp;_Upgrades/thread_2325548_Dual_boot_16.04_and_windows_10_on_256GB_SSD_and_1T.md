---
title: "Dual boot 16.04 and windows 10 on 256GB SSD and 1Tb HD for data"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by SteveTyrer on 2016-05-23
[FONT=arial]Hi [/FONT]
[FONT=arial]I have been using Ubuntu for about about 6 year and installed the system on various computers as a standalone operating system with no problems, now I am getting a second hand [/FONT][COLOR=#333333][FONT=Helvetica neue][B]
[SIZE=2]"Lenovo IdeaPad Y580, 1TB HD, Crucial 256GB SSD" [/SIZE][/B][/FONT][/COLOR]It has windows 10 installed on the SSD and I wish to set the machine up to dual boot with both W10 and 16.04LTS on the 
SSD for speed and all the data on the 1TB HD.
Can someone please give some advice on how to do this?

Thanks in anticipation  Steve

---

### Post by yancek on 2016-05-23
You would first need to determne if windows is installed UEFI.  If pre-installed then it is very likely that it is.  You can check that by using the command shown at the link below which also gives an explanation of dual booting using UEFI.  You would need to identify which /device is the SSD and which the 1TB which should not be difficult.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-05-23
Only use Windows to shrink the Windows NTFS partition and reboot immediately so it can run chkdsk.
Make sure Windows fast start up or hibernation is turned off.
Be sure to boot installer in UEFI mode, link above by yancek shows both boot screens. Your UEFI should offer two boot options one UEFI:name and other just name which is BIOS boot.
You want Ubuntu in the same boot mode as Windows either UEFI or BIOS, but Windows is probably UEFI, so you will want Ubuntu in UEFI boot mode.

You have a couple of choices. Either way I would have a larger NTFS partition on HDD for data. But hibernation/fast start must be off or it also is hibernated and then not accessible from Ubuntu.
You can put /home on HDD during install, or you can leave /home inside / (root) on SSD and have a large data partition on HDD. 

Back when I had XP, I had two data partitions, one NTFS & one ext4 for Linux data. Bit less confusing now with just the large ext4 data partition as all data goes there as I have no Windows to share with. :)

More details in link in my signature below.

---

### Post by SteveTyrer on 2016-05-23
Thanks yancek and oldfred for your help which if very much appreciated :D.

---

### Post by Mark Phelps on 2016-05-23
Any PC that comes with Win10 preinstalled will certainly have FastStartup already enabled -- and that is a problem.

FastStartup forces Windows to go into hibernation even if you choose Shut Down and when this happens, all open partitions remain mounted, preventing access to those partitions from outside the Windows OS that was running.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by SteveTyrer on 2016-05-23
Thanks Mark a good point and duly noted.

---

### Post by SteveTyrer on 2016-05-25
Thanks for all the help, 16.04 installed alongside W10 with no problems :D

---

