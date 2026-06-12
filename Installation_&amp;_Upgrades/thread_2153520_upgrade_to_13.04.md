---
title: "upgrade to 13.04"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by quarkhirad on 2013-06-11
Hi i visited [http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade) to learn how to upgrade from 12.10 to 13.04. Now i dont have update manager instead i have software updater in my dash. However when i open terminal and type update-manager it opens the same thing as software updater from my dash. Hence i assume it is the same thing. It checks for updates and after downloading some files it just say your system is upto date. Their is no option for upgrading.Help how do i upgrade.

---

### Post by slickymaster on 2013-06-11
To upgrade it's easy, just open your terminal and run the following command:```
do-release-upgrade
```

---

### Post by coffeecat on 2013-06-11
If you want to use Software Updater to upgrade to 13.04, open Software Updater and then click on the settings button. A new window will open - click on the updates tab. Look for "Notify me of a new Ubuntu version" near the bottom. If you are not being prompted for the 13.04 release it is probable that this is set to "For long-term support versions." If so, change the drop-down to "For any new version", and close the tabbed window. Software Updater should then prompt you for upgrading to 13.04 after it has updated the metadata.

---

### Post by quarkhirad on 2013-06-11
coffeecat

Hi i am sorry i forgot to metion that i already checked the settings it says any new verssion still i am not able to upgrade.

---

### Post by quarkhirad on 2013-06-11
slickymaster

Hey hi thanks that actually works. I am downloading the packages as i am typing 1073Mb.

---

### Post by Icetoad on 2013-06-11
The foolproof way is to download the iso, use unetbootin to make a boot disk(usb), and reboot system.
boot from the disk(usb), upgrade to 13.04. :)

---

### Post by Bucky Ball on 2013-06-11
*Thread moved to **Installation & Upgrades**.*

Unsure why this was in ***Absolute Beginners*** ...

You will have better luck posting under the correct category. Cheers. ;)

---

### Post by Bucky Ball on 2013-06-11
*Thread moved to **Installation & Upgrades**.*

Unsure why this was in ***Absolute Beginners*** ...

You will have better luck posting under the correct category. Cheers. ;)

---

### Post by quarkhirad on 2013-06-11
> **slickymaster said:**
> To upgrade it's easy, just open your terminal and run the following command:```
do-release-upgrade
```

Hey hi yeah i got it running and then my net failed for some reason.Now that i have my net back i typed the command in terminal except this time it says no new releases found. 

I then typed update-manager in terminal and after downloading some stuff it says 

Not all upgrades can be installed

Run a partial upgrade to install as many updates as possible

This can be caused by:

Aprevious upgrade wich did'nt complete 
problems with some of the installed software
unofficial software packages not provided by ubuntu 
Normal changes of a pre-release verssion of ubuntu

If i click continue it gives me a list of packages. At the bottom it says 786Mb to be downloaded. This figure is off as when itried using the terminal with command do-release-upgrade it gave me a figure of 1073Mb  and i had downloaded only around 80 Mb of files. Please help. How do i get my upgrade process back on track.

---

### Post by slickymaster on 2013-06-11
> **quarkhirad said:**
> Hey hi yeah i got it running and then my net failed for some reason.Now that i have my net back i typed the command in terminal except this time it says no new releases found. 

I then typed update-manager in terminal and after downloading some stuff it says 

Not all upgrades can be installed

Run a partial upgrade to install as many updates as possible

This can be caused by:

Aprevious upgrade wich did'nt complete 
problems with some of the installed software
unofficial software packages not provided by ubuntu 
Normal changes of a pre-release verssion of ubuntu

If i click continue it gives me a list of packages. At the bottom it says 786Mb to be downloaded. This figure is off as when itried using the terminal with command do-release-upgrade it gave me a figure of 1073Mb  and i had downloaded only around 80 Mb of files. Please help. How do i get my upgrade process back on track.

First make sure you have evrything important backed up. Then try:```
sudo apt-get install -f
```If that runs without errors then:```
sudo apt-get update && sudo apt-get dist-upgrade
```Note that is **dist-upgrade** not do-release-upgrade. Let us know what happens.

---

### Post by quarkhirad on 2013-06-13
> **slickymaster said:**
> First make sure you have evrything important backed up. Then try:```
sudo apt-get install -f
```If that runs without errors then:```
sudo apt-get update && sudo apt-get dist-upgrade
```Note that is **dist-upgrade** not do-release-upgrade. Let us know what happens.

Hey thanks i am running 13.04. The interesting thing is when i restarted the system after the upgrade i had everthying the same in looks my desktop log in etc. Thats cool :P.

---

### Post by slickymaster on 2013-06-13
You're welcome.
> **quarkhirad said:**
> Hey thanks i am running 13.04. The interesting thing is when i restarted the system after the upgrade i had everthying the same in looks my desktop log in etc. Thats cool :P.
That's what's expected, since you just perform an upgrade to your system, not a reinstall.

---

