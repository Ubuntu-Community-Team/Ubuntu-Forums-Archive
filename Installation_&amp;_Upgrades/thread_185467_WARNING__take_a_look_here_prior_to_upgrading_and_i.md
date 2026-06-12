---
title: "WARNING / take a look here prior to upgrading and installing!"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-05-31
**WARNING / take a look here prior to upgrading and installing!**

**I'm posting this as a forum user and not as a staff member. This is all on your own risk. Please be careful.**

There are two sections : section [i] is regarding to installing and section [ii] is regarding to upgrading.

**section [i] : READ THIS PRIOR TO INSTALLING DAPPER :**

Download the cd image here : [http://www.ubuntu.com/download](http://www.ubuntu.com/download) 
You should probably download the desktop or alternate install cd.
Installation instructions are found here : [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)
You can find further burn instructions here : [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
Burn the cd "as an image" on a 700 mb cd. Don't try to burn it on a 650 mb cd. 

[http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2) 
[quote=frodon]
With the desktop CD, at the partition step when you edit manually the partitions and create your root and swap partition you may not be able to select the partition you created for the swap in the next step.

I waste 30min to understand why and to find a workaround.
To avoid this problem open gparted before the install (System > Administration > Gnome Partition Editor) and create your partitions then once done run the installer and the problem is gone.

This problem may happen performing a fresh install with the Desktop CD and it seems that i'm not alone in this case : [http://ubuntuforums.org/showthread.php?t=186309](http://ubuntuforums.org/showthread.php?t=186309)
[/quote]

**section [ii] :READ THIS PRIOR TO UPGRADING TO DAPPER :** :
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

**You should close all applications during upgrading to Dapper. If you don't your system might become unresponsive.**

You should also **disable screen savers/lock** before upgrading. See here for someone who had troubles because of it :
[http://www.ubuntuforums.org/showthread.php?t=187022](http://www.ubuntuforums.org/showthread.php?t=187022)

**You should remove docbook-utils before upgrading. **
$sudo apt-get remove docbook-utils
for more information see here :
[http://www.ubuntuforums.org/showpost.php?p=1092990&postcount=37](http://www.ubuntuforums.org/showpost.php?p=1092990&postcount=37)

During dist-upgrading from Breezy to Dapper **non-official repos should be commented**. Dist-upgrading using the update-manager tool is easy as it comments all non-official repo's automatically.

good luck! :)

Most of the times the update-manager works fine. I recommend this method of dist-upgrading to non-experienced users. **Personally** I prefer doing it "by hand" using the commandline.

**If** you need to dist-upgrade by hand. Here's some information. **dist-upgrading by hand :**

[I]**First backup your personal files if you haven't done so.**

And backup your sources.list :
$sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

Change breezy to dapper and make sure to **comment all non-official repositories**.Or use this clean Dapper sources.list :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

to edit your sources.list :
$sudo gedit /etc/apt/sources.list
Or from the terminal :
$sudo pico /etc/apt/sources.list

get into ctrl-alt-f1

$sudo apt-get update

It happens quite often that this command wants to remove ubuntu-desktop / kubuntu-desktop so don't worry. 

$sudo apt-get dist-upgrade

Make sure everything is installed by :
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop (or kubuntu-desktop / edubuntu-desktop / xubuntu-desktop)

Now do a reboot and you should be dist-upgraded from breezy to dapper.
[/I]

About Dapper :
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

**Please post your tips and/or fixes here :**
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

**Are you having problems ? Read this first :**
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

If you have problems and you need help IMHO it's best to start a new thread. In your own new thread : be elaborate about your problems. **Post the errors you get.** Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

**edit :**
I changed uncommented to commented. I hope it was obvious that in order to disable non official repo's those repo's have to be **commented** in the sources.list.

---

