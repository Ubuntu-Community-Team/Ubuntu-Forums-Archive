---
title: "Installed through terminal in ubuntu and it works. USB Linux mint does not"
date: 2016-02-03
forum: MINT
---

### Post by jcer93705 on 2016-02-03
Hello guys. I have a problem here. I installed Ubuntu gnome on my laptop and works well. Installed other graphic envirement what ever it's called. Like Unity, KDE, and Linux Mint Cinnamon. But now that I love it so much. I want to reinstall but Just Linux Mint Cinnamon. I burned into a DVD also into a thumb drive. But hit a snag. Here the video. Hope somebody can help me. Ty 

[https://www.youtube.com/watch?v=TWC4g2GWW6c&feature=youtu.be](https://www.youtube.com/watch?v=TWC4g2GWW6c&feature=youtu.be)

---

### Post by jcer93705 on 2016-02-03
I'll boot up with nomodeset if not then nouveau.noaccel=1 let see how it goes. I have Nvidia GTX 965M

---

### Post by yancek on 2016-02-03
Did you download the Mint iso from the Mint official site?
Did you do an md5 checksum on the downloaded iso file to verify it's integrity?
What software did you use to put the Mint iso on the flash drive?
Trying nomodeset would be a good first test option.  If you have windows installed UEFI, then you must install Mint UEFI or one of the systems won't work and possibly neither will work.  Mixing an MBR install with a UEFI just doesn't work so don't even try that.  The reasons are explained at the Ubuntu documentation site below:

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You might also turn off anything relating to fast boot or hibernation which is the default with windows 8 and newer.

---

### Post by jcer93705 on 2016-02-04
> **yancek said:**
> Did you download the Mint iso from the Mint official site?
Did you do an md5 checksum on the downloaded iso file to verify it's integrity?
What software did you use to put the Mint iso on the flash drive?
Trying nomodeset would be a good first test option.  If you have windows installed UEFI, then you must install Mint UEFI or one of the systems won't work and possibly neither will work.  Mixing an MBR install with a UEFI just doesn't work so don't even try that.  The reasons are explained at the Ubuntu documentation site below:

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You might also turn off anything relating to fast boot or hibernation which is the default with windows 8 and newer.

Hi I ended up solving the problem with nouveau.modeset=0 I boot up and installed the os I reboot and booted fresh install wont start
then I did it again with that code then it entered to the os without accelerator then installed graphic driver rebooted no problem no need
the code anymore. Now I do have a new problem how ever. Sound and mic doesn't work and not sure if mic works. Oh and track pad doesn't work. But with Ubuntu Gnome 15.10 and Unity of 15.10 version everything works. Should I start a new subject?

---

