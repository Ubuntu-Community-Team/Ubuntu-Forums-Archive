---
title: "Trouble with booting 12.04 CD / installing Boot Helper"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2012-04-26
Hello, I got [some issues]("http://ubuntuforums.org/showthread.php?t=1965879") after upgrading from 11.10 to 12.04 (both 64-bit) today, so decided to do a clean install instead. Downloaded the CD, burned it, but it's not recognized by the system to boot from it. Ran Boot Helper from the CD, but after its installation completes, this error message pops up:

[http://i.imgur.com/91AYT.png](http://i.imgur.com/91AYT.png)

Is there any way I can solve this installation issue, or get the CD boot otherwise?

---

### Post by Tornikee on 2012-04-27
Any hints? I'm sure this shouldn't be hard to solve, if it's not a global issue w/ 12.04 Live CD.

---

### Post by zdeuyo on 2012-04-27
> **Tornikee said:**
> Any hints? I'm sure this shouldn't be hard to solve, if it's not a global issue w/ 12.04 Live CD.

Hello,

Are you installing Ubuntu to Wubi or on a separate partition? Also, please clarify your issue more if possible. Look forward to helping you.

---

### Post by Tornikee on 2012-04-27
Thans for your reply. I'm installing it on a separate partition - I've done Ubuntu installations this way for a year, and there were only a couple of instances where the Live CD wasn't recognized upon booting, but these issues were solved by installing the Boot Helper. This time though, the error shown above makes this solution not possible.

I tried burning the CD in two ways Window$ offers you: 'use it as USB' and 'use it as CD'. Neither option solves the issue of the system not recognizing the CD as bootable.

---

### Post by garvinrick4 on 2012-04-27
Your .png shows you are installing WUBI which is a folder in Windows right next to USERS in C: Drive.

So this is not a partition install

Put CD in tray and then reboot, if BIOS is set to see CD first in line in front of hard drive then you can install
in a partition. 

Make sure you have uninstalled any folders in Windows that has UBUNTU as its name.

---

### Post by Tornikee on 2012-04-27
BIOS is definitely set to boot from CD first, but even when I don't run the wubi autorun from this CD and just restart the PC, the CDis not recognized as bootable. The system just heads to Boot OS selection menu.

---

### Post by lisati on 2012-04-27
> **Tornikee said:**
> BIOS is definitely set to boot from CD first, but even when I don't run the wubi autorun from this CD and just restart the PC, the CDis not recognized as bootable. The system just heads to Boot OS selection menu.

Did you remember to [burn the ISO]("https://help.ubuntu.com/community/BurningIsoHowto") file as a disk image?

---

### Post by Tornikee on 2012-04-27
> **lisati said:**
> Did you remember to [burn the ISO]("https://help.ubuntu.com/community/BurningIsoHowto") file as a disk image?
Oh that should be the cause of the issue. I used the other way (burning .ISO contents, not the .ISO file, onto the CD) for 11.10 so thought that was the way to use it for 12.04 too.

Thanks for the hint, will try going that way as soon as I'm back home later today.

---

### Post by Tornikee on 2012-04-27
My Window$ 7 didn't have the soft w/ the 'Burn image' command, so I followed the guide for other Window$ versions, installed the InfraRecorder, burned the .ISO as image, and the system successfully booted the CD. Thanks for the assistance.

---

