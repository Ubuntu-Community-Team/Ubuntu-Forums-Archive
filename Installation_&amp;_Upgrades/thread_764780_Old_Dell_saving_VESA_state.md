---
title: "Old Dell saving VESA state"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by TheMemphisExperience on 2008-04-24
Got an old dell here with the bare minimum to run Xubuntu. I've got 7.10's live cd in there, but it is hung at "saving VESA state". I have to go to work now, but hopefully someone will be able to tell me if there is a chance it will work or if I can test connect to the internet before doing a full install.

Cheers!

---

### Post by dstew on 2008-04-24
It might be running out of memory. If your memory is less than than 128 MB, you should install Xubuntu using the Alternate Install CD. But Xubuntu won't run very well with less than 128 MB.

If you have enough memory, there are other reasons for the Live CD to fail. It might be a bad burn. You should check the integrity of the CD (opening menu choice). If the CD is OK, it might be having trouble with your hardware, usually graphics display adapters. That might be the case here. You can try booting in Safe Graphics Mode, another opening screen menu choice. If none of this works, consider installing using the Alternate Install CD. It installs the same Xubuntu desktop using a text-based installer that is easier on the system.

---

### Post by TheMemphisExperience on 2008-04-24
> **dstew said:**
> It might be running out of memory. If your memory is less than than 128 MB, you should install Xubuntu using the Alternate Install CD. But Xubuntu won't run very well with less than 128 MB.

If you have enough memory, there are other reasons for the Live CD to fail. It might be a bad burn. You should check the integrity of the CD (opening menu choice). If the CD is OK, it might be having trouble with your hardware, usually graphics display adapters. That might be the case here. You can try booting in Safe Graphics Mode, another opening screen menu choice. If none of this works, consider installing using the Alternate Install CD. It installs the same Xubuntu desktop using a text-based installer that is easier on the system.

I went into the BIOS before trying any Ubuntu magic. At 192, it be ok. I'll try the safe graphics mode. 

I am hesitant to overwrite XP as it is not my computer, but someone elses which they will give to someone else. I don't want to have to buy them some windows OS or such nonsense.

 The thing I need to know is if it can connect to the internet using this plugin wireless card she jammed in there. Apperently it used to work, but doesn't anymore. She just wants internet. With the whopping 6 GB HDD, there isn't room for too big a library of much.

 If I knew it would work, I would just slap the 8.04 alternate CD I have in there.

---

### Post by dstew on 2008-04-24
I think you can use the Alternate Install CD to install the Xubuntu desktop if you can connect to the internet. You would install the 8.04 Server (base install -- I think it is a menu item on the Alternate Install opening menu). The Server install is just a command line system. Once it is installed, you might have to set up the internet connection using command-line tools. Once you have an internet connection, you can install the Xubuntu desktop by```
sudo apt-get install xubuntu-desktop
```It will fetch the packages over the internet, and install them. Once they are installed (might take an hour or so) enter **startx** or reboot to get a desktop.

Of course, this depends on being able to connect to the internet. Wired connections are usually a sure thing, but the wireless might not work easily. Do you know what kind of wireless card it is?

Anyway, installing the Server edition of 8.04 is probably safe, and at least you would have a command line to play around with.

---

### Post by jarven on 2008-11-04
Following worked for me
[http://ubuntuforums.org/showthread.php?p=6101939#post6101939](http://ubuntuforums.org/showthread.php?p=6101939#post6101939)

---

