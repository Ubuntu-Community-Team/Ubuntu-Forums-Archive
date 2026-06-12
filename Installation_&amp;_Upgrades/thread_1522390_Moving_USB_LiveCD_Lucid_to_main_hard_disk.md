---
title: "Moving USB LiveCD Lucid to main hard disk"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by ypestis on 2010-07-02
Hello, im running Lucid from my USB key at the moment and configuring and playing around a bit and I was wondering if it is possible to move this install to my main harddisk so I can keep all installed apps and configurations

---

### Post by garvinrick4 on 2010-07-02
> **ypestis said:**
> Hello, im running Lucid from my USB key at the moment and configuring and playing around a bit and I was wondering if it is possible to move this install to my main harddisk so I can keep all installed apps and configurations
 Sorry you can only install the original .iso file on an install. Nice thought though.

---

### Post by ypestis on 2010-07-02
Oke, what about installing Lucid to the main drive and after that copying over the USB installation files manually? Bad Idea probably?

---

### Post by garvinrick4 on 2010-07-02
Start by installing;
```
sudo apt-get install ubuntu-restricted-extras gconf-editor gparted startupmanager && sudo apt-get update && sudo apt-get upgrade
```This will get you; flash, ttfonts, codecs, java and more in ubuntu restricted extras and a few more essentials you can see and update and upgrade. While this is going on do your panels and things in your Preferences, keyboard shortcuts, power management and others you want. Will make things quicker. Just copy and paste. Enjoy and do not forget to get your internet connection first.

---

### Post by garvinrick4 on 2010-07-02
[LIST]
[*]When done run this and it will give you a text copy of all your installed packages in
[*]their true linux names, comes in handy.
[*]```
sudo dpkg --get-selections > installedsoftware
```
[*]Will be in Home folder[URL="http://ubuntuguide.org/wiki/Ubuntu:Lucid#networking"]  
[/URL]
[*]
[*]Users guide:
[*][Ubuntu:Lucid - ]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#networking")
[/LIST]

---

### Post by C.S.Cameron on 2010-07-02
What kind of install do you have on your USB disk? If it is a full install you can move it to your hard disk. Even if it is a persistent install, (usb-creator, UNetbootin), it should be possible.
It is easy to also copy just your home folder.

The dd command will clone a partition from a flash drive to a hard drive.
If the flash drive was bootable the clone will be also.

The dd command is very powerful and can easily overwrite everything on your hard disk if used improperly.

You should back everything up, and study the command, start with:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

I would suggest practicing with an old blank HDD first.

Edit
I have just tried dding a Live USB to hard disk and it works.

---

### Post by C.S.Cameron on 2010-07-02
On second thought, every change made to a persistent flash drive is stored in a file named casper-rw.
If you do a frugal install to hard drive you should be able to just copy casper-rw from /cdrom on the flash drive to /cdrom in the frugal install.


A bit more complex, you can mount casper-rw and use the files inside to overwrite the files on a hard disk install, see:
```

http://ubuntuforums.org/showthread.php?t=1028564
```

---

