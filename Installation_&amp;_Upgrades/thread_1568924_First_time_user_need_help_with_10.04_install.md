---
title: "First time user need help with 10.04 install"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by Notn4 on 2010-09-06
I'm pretty much a complete first time user, I've had an ubuntu live cd that I've used for maybe 5h when my PC was messing with me and I needed to check if the random reboots were hardware related or if it just was the OS, anyway, I got a few days ago another desktop PC, it's not the newest in the world so I decided to install ubuntu on it and start exploring something else than Windows :)

The live CD that I had would not install so I tried downloading the newest one and burn it to an CD, burned it at 4x speed and used a better kind of CD, not some shitty brandless ones, still nothing...

The installation freezes at random steps, usually at step 2, where I'm supposed to tell the installer "where I am" to set the clock etc. when clicking forward it just freezes, once I got to step 5, when it asked for user info, then it froze again, I even left it on over night but still nothing when I woke up :(


and also the installer is extremely slow, is that normal? I mean like 15mins to boot up the installer? and then having to wait 15-30mins between steps?

The PC I'm trying to install Ubuntu on is an old HP Pavilion with 
AMD Athlon XP 3000
256Mb DDR


and also, Im trying to install Ubuntu as my main OS, I want the whole HDD formatted, is the installer capable of doing this?

---

### Post by krimzonstarr on 2010-09-06
First off, welcome to the world of Ubuntu! I am not an expert, but I will try and direct you to some useful resources.

1. My favorite tip for installation problems, iso and disc integrity. I have personally had so many problems with iso's being corrupted while downloading, burning, LiveUSB creation, and while it doesn't seem to hit most users, it hits me all the time. Follow the guide at [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") and make sure that the iso file and the burned disc match the checksums. Even if the LiveCD boots, there may be errors preventing installation.

2. If the checksums match up, time for attempt number 2. I have seen many post where people have been having issues with their graphics cards preventing installation or boot up. You can try the guide at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") Workaround A seems to be the usual fix.

3. If those methods don't fix the problem, then hopefully someone more knowledgeable will stumble upon your post!

4. Once the installer is up and running, there will be options to partition your hard drive. Ubuntu is fully capable of being installed side-by-side with Windows, or using the entire drive. Good luck!

---

### Post by nothingspecial on 2010-09-06
Sounds like you don`t have enough ram for the installer.

If you have a wired internet connection, you may have more luck with a minimal install.

---

### Post by mörgæs on 2010-09-06
Yes, install the minimum Ubuntu from this ISO:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

After that, type

```
sudo apt-get install ubuntu-desktop
```

or 

```
sudo apt-get install lubuntu-desktop
```

if you want something lighter. It will not be a speedy system with 256 MB memory, but it will work. Remember to have wired access during the entire process.

---

