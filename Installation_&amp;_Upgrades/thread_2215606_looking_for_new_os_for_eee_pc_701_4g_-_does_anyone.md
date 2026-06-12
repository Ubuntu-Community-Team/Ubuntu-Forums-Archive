---
title: "looking for new o/s for eee pc 701 4g - does anyone still use theirs"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by interglossa on 2014-04-07
I have Ubuntu 10.04 running on my asus eee pc 701 4g from 2007 but it does not support HTML5
so I am not able to use the Naxos Music Library.  Has anyone continued to use their eee pc 701?

I see some postings about being able to install ubuntu and xubuntu 12.04 but in the interim people
have also tried using android and chromium os.  Does anyone have any thoughts on this?

---

### Post by coldraven on 2014-04-07
I have the eeePC 900 and it is running Xubuntu 13.10 very nicely. It has two internal drives, a 4Gb (supposedly fast) drive for the OS and a 16GB (slower) drive for user data. (in my case /home)
A "normal" install of Xubuntu will almost fill the 4GB drive. After a short time there is no space for updates to be downloaded and uncompressed.
I solved this by creating two 1GB partitions on the 16GB drive and making one /tmp  and the other /var 
I thought that it was too complicated to do this on the existing installation so I just did a fresh install. 
I used gparted during the install to create the partitions / (root), /tmp, /var and /home
So far it is working perfectly :)

Your problem is that you only have a 4GB drive. If you leave a reasonably large SD card permanently in the slot you could probably do the same as I have.

This is just a guess, so I hope that someone else will give us their take on the problem.

---

### Post by sudodus on 2014-04-07
These alternatives are worth trying:

***Lubuntu 13.10*** or the next version Lubuntu Trusty, to become ***Lubuntu 14.04 LTS*** in a week or two. It is important to keep the system small, and the installation process with the conventional installers might have problems due to the small drive. But the size of the final installed system is small enough to run in 4 GB SSD.

One alternative is to use the ***One Button Installer*** and install Lubuntu 13.10. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2172971"]
One Button Installer, 'OBI'[/URL]

If you want something really light you can install the basic system of ***Lubuntu Core Trusty*** using the experimental ***9w*** installer. See this link, posts #88 and #89 and the following

[http://ubuntuforums.org/showthread.p...6#post12957586]("http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586")

and you can install packages  afterwards to get exactly what you want. You can even start with a text  mode system.

The OBI is made to be installed from USB, and 9w can be installed from USB. In both cases the shell-script ***mkusb*** can be used to create a USB boot drive from the OBI image file or the 9w iso file.

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

-o-

If you think the methods above are too complicated, or you want smaller systems, you can try to install some really small linux distro, ***puppy, tiny core, slitaz*** or ***DSL***, or simply run 'any' system live (booted from USB) instead of installing a system.

---

### Post by interglossa on 2014-07-30
Thanks for your responses which I carefully digested.  I ended up going with a careful update of the Ubuntu 10.04 which was already on my asus eee pc 701.  I also have an eee 900 but I have had problems with it so I probably won't be upgrading it.  I think those of us who are still using the eee are a rare breed indeed, but I find my 701 has survived bike rides and winter temperatures remarkably well.

---

### Post by sudodus on 2014-07-30
Are you still running 10.04, or did you upgrade it carefully into 12.04 LTS?

Remember, there are no updates, not even security updates for the desktop packages of 10.04. Only the packages in common with Ubuntu Server 10.04 are still supported, so you are on your own concerning security.

---

### Post by interglossa on 2014-07-30
I know, but I am concerned about running out of space on my 4GB system.

---

### Post by sudodus on 2014-07-31
If you have a 4GB USB pendrive, you can use it and install various versions and flavours of Ubuntu and maybe other distros for testing, what would work well in only 4 GB.

So install not into the internal 4 GB drive but into the 4GB USB pendrive. See thiese links
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

And you can select what kind of system to install, for example Lubuntu Core. The size depends on how much you install. You can also decide manually what packages you need and want to install from the very basic fundament of the text mode system.

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

And when you have found a good system, install that into the internal drive.

---

### Post by interglossa on 2014-07-31
Those are great links.  The Try Ubuntu should be a sticky post in the Tutorials forum.  Thank you!

---

### Post by sudodus on 2014-07-31
I'm glad the links are useful for you :-)

If you want faster action also during the installation, you might want a fast USB pendrive. You might even prefer to run the computer from a fast 16 GB USB pendrive. In that case, remember to add the mount option noatime in /etc/fstab to reduce wear. You should also avoid using swap except as an emergency in special cases, so don't use several tabs when browsing the internet, and close programs that are not used.

See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

