---
title: "Can't See Primary Drive"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by dkolok on 2008-10-11
Just installed Ubuntu 8.04 on primary drive with WinXP. Booting to Ubuntu, Ubuntu shows secondary (slave) drive, but not primary drive. Both drives are IDE, NTFS, and show in BIOS on AUTO. In Ubuntu, Ubuntu gives notice of application package, but error happens and just list of packages I can install appears. (I have not installed any.) Next, Ubuntu asks if want to install updates. When I click icon to OK, nothing happens. Don't know if either of these actions have anything to do with not seeing primary drive. I want to fix that first.

---

### Post by Partyboi2 on 2008-10-13
> Just installed Ubuntu 8.04 on primary drive with WinXP. Booting to Ubuntu, Ubuntu shows secondary (slave) drive, but not primary drive.How are you viewing the drive information in ubuntu? 

> Ubuntu gives notice of application package, but error happens and just list of packages I can install appears Are you able to post the error message you are getting?

---

### Post by dkolok on 2008-10-13
Pop-up advising to install packages didn't appear last boot. Was able to install the 128 updates. "Computer" shows only secondary HD.

---

### Post by Partyboi2 on 2008-10-13
Does under "Computer" show  a icon with the name "Filesystem" ? If it does, that is your primary hard drive.

---

### Post by Elfy on 2008-10-15
Are you using wubi - or installed to it's own partition.

If wubi - then check in /hosts which is where you should find the rest of the windows drive

---

### Post by dkolok on 2008-10-15
Have wubi; found primary drive at File System, Hosts. Thanks. As new user have number of other questions finalizing installation, if I may ask.

Have dual monitors with Windows; possible with Ubuntu? (Extended desktop; not same info on both monitors.) (I know about the virtual desktops.)

Command to arrange panels horizontally or vertically, as with Windows?

Have Ubuntu 7.04 on CD, but wouldn't boot, so downloaded wubi. Changed drive sequence in BIOS; didn;t help, nor did booting to boot sequence. Fix, if I waned to use CD? 

Was using GoBack with Windows (XP); can't use with dual boot. Program available similar to GoBack that'll handle dual boot?

Way to eliminate calls for Administrative password in Ubuntu? I'm only one using computer.

Ubuntu doesn't fill screen, as does Windows. Fix, without changing monitor settings each time switch?

---

### Post by Elfy on 2008-10-16
Dual monitors are possible yes - you'd need to make sure that the driver is installed for your graphics card. Check in Hardware Drivers in System > Admin menu if there is one for your card. Once you've done that it might be possible to arrange your screens as you wish, without knowing what card it is hard to tell. Installing the card will also deal with the last point.

No idea about GoBack.

Password for admininstration is the way it is for a reason, there are ways to stop it but the forum policy is to not give help. Once you've got the system set up you shouldn't need to use it much.

Booting with the cd - it must be burnt as an image - not as a data disc. If your pc is set up to boot from cd first or you have the option to choose and it won't boot the cd then I would suspect it has been burnt incorrectly.

IT would be best to start threads on these things rather thna keep adding new problems to this one.

---

