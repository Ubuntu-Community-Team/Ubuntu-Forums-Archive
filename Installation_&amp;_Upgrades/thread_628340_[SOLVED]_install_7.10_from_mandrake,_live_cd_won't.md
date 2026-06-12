---
title: "[SOLVED] install 7.10 from mandrake, live cd won't start or go into liveCD"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by toriam2006 on 2007-12-01
I ran 6.10 for 6 months, got comfortable with Linux, then decided to upgrade to Gutsy. Downloaded the text/alternate Cd, ran it, followed the instructions about emptying usr/X1186/bin (an error msg?). It still wouldn't install corectly, so I rebooted, it was fine, i shut down. started up the next day, there's a big problem, won't boot correctly, says X server won't initalize for graphics. Won't initalize much at all! So I find some Mandraske 2005 Limited Edition install disks I have, I install that. I fool with it a few days, decide I prefer Ubuntu, download 7.10 LiveCD.  When I put it in the drive and reboot, it won't start like its supposed to. The CD drive is set to boot first, i tried to click  on the icon, no luck. I looked for an md5sum, no luck there either? What should I do now to install?

---

### Post by ajgreeny on 2007-12-01
How did you burn the iso file?  You must burn it as a CD image not just as a file.  Have a look at the CD using a file manager in windows, or mandrake if you still have it.  If it just shows the single file you have a useful coaster for your coffee cop, but not much use as an install CD.

Try reburning with mandrake or windows but make sure you use the CD image option this time, not burn as a data disk.

Have a look at this info as well for the md5sum of the download.  You can check the iso file is OK in mandrake using the terminal.  Just cd to the folder where the iso file is and then enter ```
md5sum ubuntu-7.10-desktop-i386.iso
```and hit enter.  Terminal will tell you the md5sum of that file and you can check it with the md5sum in the site here:-
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by toriam2006 on 2007-12-01
I am sure the cd is in the correct format, the md5sum is correct (thx 4 reminding me where they were!). The cd is recognised, shows up on the dsktp in mandrke, just when I reboot or shut down and restart the computer doesn't seem to see it. It did give me the proper ubuntu livecd startup screen for a little while last night, but it said there was an error, an IO error I beleive, for every option I tried to start under. A last resort, but if I wipe and initalize my HD, can I run the install?

---

### Post by ajgreeny on 2007-12-02
> A last resort, but if I wipe and initalize my HD, can I run the install?I don't see why that should make a scrap of difference if your machine is not booting from the CD.

---

