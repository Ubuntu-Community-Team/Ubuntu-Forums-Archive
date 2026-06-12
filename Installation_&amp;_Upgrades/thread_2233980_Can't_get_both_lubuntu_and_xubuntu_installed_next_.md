---
title: "Can't get both lubuntu and xubuntu installed next to windows"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by Ralf_Hutter on 2014-07-11
Hello everybody, i got a computer with windows on it but want to use xubuntu. I installed lubuntu and let windows as it was, just in case i might need it once. My plan was to download the components necessary for xubuntu and then switch, and be able to switch between lubuntu and xubuntu at any time, as i had been doing on another computer before. But now, when i start the computer, i can only choose between "Ubuntu", "more options for Ubuntu", "Memory test" and Windows. Going for "more options for Ubuntu" just lets me choose between 3 different kernels, as i understand it: "Linux 3.13.0-30-generic" or 29-generic or 24-generic, each of it also possible in a "recovery mode". None of them leads to xubuntu (i didn't try the recovery modes, though). Xubuntu is downloaded as it should be. I did it via synaptic, and the ubuntu download centre also shows it is installed. Why can't i choose it in the booting menu? [http://ubuntuforums.org/images/smilies/icon_mad.gif](http://ubuntuforums.org/images/smilies/icon_mad.gif)

---

### Post by TheFu on 2014-07-11
Did you do 3 installations or just load the xfce4 and lxde packages into the same OS install?  To choose a different DE, on the login screen, click on the "gear" and select the one you want BEFORE typing in your login credentials.

---

### Post by grahammechanical on 2014-07-11
What you are describing is the Grub menu with the options Ubuntu; Advanced options for Ubuntu; etc. As far as I know when we install any of the flavours of Ubuntu the Grub menu will report it as "Ubuntu."

If you have installed Xubuntu and Lubuntu as well as Windows then the Grub boot menu should show something like

Ubuntu
Advanced options for Ubuntu
Memtest
Memtest+serial
Windows bootloader on sda?
Ubuntu 14.04 on sda?

One Ubuntu would be Xubuntu and the other Ubuntu would be Lubuntu. If you only have one Ubuntu then load into it and open a terminal and run

```
sudo update-grub
```

and see if on a re-boot you get an option to load another Ubuntu.

Regards.

---

### Post by Ralf_Hutter on 2014-07-12
Thanks to both of you. To update the grub boot menu didn't help. To TheFu's question: The first install of Lubuntu didn't work, i had to abort it, and afterwards try several times, so maybe that's why there are three installs (which doesn't explain,though,why there should be 3 different versions).
But this whole thing is interesting, i hope you're enjoying yourselves.
First of all, what i didn't mention: Ubuntu doesn't even ask me a password. So there's no chance i can change/choose the desktop i like in the booting process.
But now i tried to change the user after booting, and indeed then i can change also the desktop environment. But with strange results: 
1. When i leave Lubuntu by clicking on "change user", the menu for choosing the desktop environments is blocked, if i want to login with my normal account, which has admin rights. If i choose another account or even a guest account, the menu is free and i can choose both xubuntu and xfce session.
2. If i leave Lubuntu by clicking on "logout", i can choose any DE with any username.
Weird!
But that is not all. If i choose Xubuntu, i have a lot less features and programmes in the systems setting menu etc than i have when choosing xfce and even Lubuntu. I don't understand that. Even some programmes, like deja-dup, that synaptic shows me are there, are not shown in the start menu when i choose Xubuntu session and can't be found. It seems like there's something mixed up or so.
But maybe i just stick to Lubuntu, because the new version of Xubuntu doesn't have the hidden desktop bar at the lower side that appears when you move the cursor there. That was the feature that made a practical difference.
Anyway, if anybody can explain my situation, especially why Lubuntu doesn't ask for a password at booting, i would be grateful.

---

### Post by TheFu on 2014-07-12
The OS isn't the GUI.  Learn it, know it, love it. There must be 50 different compatible GUIs for Linux.

Menus mean nothing. If they don't have all the programs, that just means that the settings for a specific menuing system wasn't updated during install. Program post-install tasks run for every package to add it to the running DE menu. I don't switch between DEs on the same install - that's a good way to get incompatible settings inside the config files that may be shared.

So - let's step back and start from the beginning. What is the output from the **boot-info** script. See my signature for links.  The goal is to understand how many installations are really on the box first.

---

### Post by Ralf_Hutter on 2014-07-14
The boot-info is here: [http://paste.ubuntu.com/7793394/](http://paste.ubuntu.com/7793394/)
Any explanation welcome!

---

### Post by TheFu on 2014-07-14
Ok - thanks for the boot-info.  What it tells me is.
* only sda6 has linux - that means 1 install.  Whatever you did to install another either
** formated the data on sda6 and installed over it OR (worse)
** did NOT format and just installed on sda6 leaving some parts mixed between xubuntu and lubuntu.

So, I wouldn't be happy.

GUIs are not the OS.  LXDE and XFCE4 and Mate and Cinnamon and Gnome3 and Unity and .... about 30 more can all be loaded onto a single Linux install.  If you want completely separate installations, then you need a different partition for each install. I wouldn't do it that way.

I would 
* perform a fresh OS install with the version you believe will be the primary.
* install the packages for any other DEs/WMs you want inside that.
* create a new userid for every different DE - so the config files for each DE don't corrupt each other. DE configs are stored by userid HOME directory.

Then changing to a different userid will let you safely change between the different environments. How?
* on the login page, click the "gear" near the password field, select the DE/WM you want to use going forward
* type in the alternate login userid
* type in the password for that userid
* login
If you place all the different DE userids into the same unix group and setup the umask for each userid to be 002, then data files created by any of these userids can be managed by the others.

However, after trying all the different GUIs, I'd pick 1 or 2 and stick with those only. It isn't like the programs installed with each GUI can't be used by the others. Programs are installed on the system, not for the GUI alone.  If you like a program that gets installed with lubuntu - just install that program for xfce or unity or kde or .... whatever.

I hope this all makes sense.

After you pick the GUI you like and pick the default GUI to use at the login, you should remove the other logins from the system - this is a security consideration, since humans are unlikely to have strong, good passwords across multiple login accounts like these.

BTW - most of my Linux partitions are 15G or smaller.  Then I create a different partition for /home (which is a best practice) and data partitions for large data - often /data is on a different machine and mounted through NFS.  Why?  Well - swapping out the OS without risking my personal data is easier this way. /home is relatively portable between Linux installations and versions.  Of course, we do have to be careful with partition numbers to ensure a new Linux install doesn't wipe /home or /data, but that isn't too hard.  50-100G for / just seems like overkill.  Even if you installed every server and GUI program, the OS wouldn't use more than 25G.

Oh - and if you dual or triple or quad-boot with different Linux installs (10G each for /), then only 1 swap partition is needed. It will be shared. OTOH, if you use virtualization and multiple Linux VMs are running concurrently, then the swap cannot be shared.

---

### Post by Ralf_Hutter on 2014-07-14
I think that's ok then. I just installed the xubuntu-desktop package on lubuntu, or, as you said: I loaded xfce4 onto lubuntu. Right? No second install then.
I guess i don't really need xubuntu, so i'll just use lubuntu the way it is now. As i won't change anything anymore now i consider your suggestions regarding the partition sizes as not so important. But thanx a lot nevertheless.

---

### Post by Ralf_Hutter on 2014-07-14
But still i wonder why lubuntu never asks for a password when booting. And, also, the booting process in not always the same. Sometimes it goes until the grub menu and i have to press enter, sometimes lubuntu starts without that.

---

### Post by TheFu on 2014-07-14
If you told it not to require a login during the install - that is why.
As far as boot stuff goes, that is controlled by grub - there are default timeouts and a default OS to boot into. That stuff is a different sort of expertise ... best to post a new question for each.  They are NOT related to each other or this thread.

---

