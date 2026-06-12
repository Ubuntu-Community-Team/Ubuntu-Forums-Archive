---
title: "Reinstalling without preserving installed packages"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by dranorter on 2013-05-08
Hi,

I'm trying to reinstall 13.04. The stage in the process where it tries to restore previously installed packages is hanging every time. The 'skip' button greys out and the terminal says something about the packages being broken. If I simply terminate the install at this point the system won't boot; it gets stuck at a black screen (with just a white underscore in the corner).

I can get the exact error message if it's helpful but what I want to do at this point is reinstall without restoring packages, since that would be faster and I mainly want to save some drawings and downloads. (I mean, sure I could take the hard drive out and back those up but honestly I've had a hard time any time I wanted to get at this laptop's hard drive.)

For anyone curious the initial reason I tried to reinstall was because 1) my wireless works flawlessly trying 13.04 on a usb drive 2) my wireless takes five or six minutes to work starting up in 12.10, including the delay while the startup screen says 'waiting up to 60 more seconds for network configuration' 3) simply upgrading the system to 13.04 didn't fix this delay.

---

### Post by darkod on 2013-05-08
The best way to reinstall without the broken packages is to format the root partition. But if your personal data is included on it (like your Home folder being inside root), you can't format until you copy the data.

You don't need to take the disk out. Simply boot the machine in live mode and copy to any usb hdd.

Otherwise, I'm not sure if you can do what you want without formatting root. The point of clean install is formatting root. Again, make sure you get your data out first!!!

---

### Post by dranorter on 2013-05-08
OK, thanks.  Fortunately I backed almost everything up a couple weeks ago; I just get paranoid that I won't know what to back up, and backing up everything takes well.. about as long as I've spent trying to do this the other way round actually.

---

### Post by ajgreeny on 2013-05-08
Just to add my 2 pence worth, I normally only backup my home and leave the rest for the OS new installation, as installing *ubuntu is so easy and quick.

If I am re-installing the same OS again, or to a different machine, I also backup the contents of /var/cache/apt/archives, as by default that contains all the .deb packages that I have installed in the past, that are still available, and it can save a lot of time, and bandwidth, when I want to install them all again.

---

