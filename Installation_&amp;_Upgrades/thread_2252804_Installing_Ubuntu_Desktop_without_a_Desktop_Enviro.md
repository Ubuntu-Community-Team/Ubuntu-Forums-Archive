---
title: "Installing Ubuntu Desktop without a Desktop Environment?"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by drew27 on 2014-11-14
[SIZE=4]**Background**[/SIZE]
I have put together my own desktop environment in Arch Linux, and I'm interested in setting up Ubuntu with the same environment. One way to do this is by installing Ubuntu Server and then adding my DE. However, I know there are packages (other than DE packages) in Desktop that are not in Server (eg. Software Center), so I'd like to install them as well.

I haven't spent that much time with Ubuntu in recent years, so I'm not totally familiar with it. My goal is to create a fully featured Ubuntu Desktop experience, except with a totally new desktop environment. I realize I can just install the entirety of Ubuntu Desktop and add another DE next to it, but I'd like to avoid that if I can. My setup includes custom Xorg and display manager settings, and I'd just like it to be alone on the system.

[SIZE=4]**Questions**[/SIZE]

[LIST=1]
[*]What are all of the packages universal to all Ubuntu Desktop versions (eg Ubuntu, Xubuntu, etc.) that are neither in Ubuntu Server nor unique to a DE? Do I just remove all of the GNOME packages from the ubuntu-desktop metapackage to get the list I'm looking for, or is there more to it?
[*]Is there a better way to accomplish my goal? For example, would it better suit a desktop PC to start by manually installing the ubuntu-minimal and ubuntu-standard metapackages rather than Ubuntu Server (then from there add the packages from question 1)?
[*]Is there anything else that you would recommend I do to set up all the bells and whistles of a typical Ubuntu installation (minus any DE other than my own)?
[/LIST]

---

### Post by sudodus on 2014-11-14
Welcome to the Ubuntu Forums :-)

I suggest that you start from the Ubuntu ***mini.iso*** (alias netboot iso file). It will give you a minimal text based system. Then you can add whichever packages you like.

Starting from a full desktop environment system may not give you a clean system. It is harder to remove packages, that were needed by some part of the desktop environment, that you want to remove.

See for example this link

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by ibjsb4 on 2014-11-14
You can use the server iso, its the same as the mini when used right.

How to :)
When you get to the screen that says 'Install Ubuntu Server', press F4 and choose 'Install a minimal system'.

Several screens later you will get to this:
[ATTACH=CONFIG]257963[/ATTACH]
Choose 'Manual package selection'.
And you end up with a terminal only (console) install.  Same as the mini iso.

From there it gets a little tricky.  Depends on your skill level and what you want to build.

Ubuntu-desktop package list:
[http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop)

This may also help.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

---

### Post by drew27 on 2014-11-15
Thanks for your replies. It looks like mini.iso is a good place to start. The server iso looks good too, but mini will save me some bandwidth. I will surely be trying out googlubuntu.com.

This from your linked article answers the second part of my first question:[quote=Lubuntu Minimal Install]A full install includes all the packages which are shipped by default with the standard Lubuntu installation . . . For the full desktop installation use . . . apt-get install lubuntu-desktop[/quote]I am still left wondering what to leave behind out of the union of every *buntu-desktop metapackage. lubuntu-core looks nice, but it still includes stuff I don't need while leaving out packages normally common to every *buntu flavor. I could install only what I have on my Arch system, but that would come short of my goal to include as much of a full featured Ubuntu Desktop as possible without including GNOME, LXDE, Xfce, or KDE.

I could write a script that cross-matches the contents of each: ubuntu-desktop, kubuntu-desktop, lubuntu-desktop, and xubuntu-desktop. I could then take the result—a list of packages common to every metapackage—and convert it into a sudo apt-get command to install everything in one go. However, there are some key distinctions. For example, Lubuntu uses lubuntu-software-center, but the others use software-center. I suppose I could create a more inclusive list by requiring packages to only be common to two instead of all four, such as xubuntu-desktop and ubuntu-desktop. **What do you think? Which two would you pick?**

It's starting to look like the only way to draw a line is by, after doing the cross-match, individually analyzing each package that is *not* common to the *buntu flavors I compared, and deciding whether they belong to Ubuntu or a DE. **Any opinions on how to more easily approximate that distinction?**

---

### Post by buzzingrobot on 2014-11-15
The core components of Ubuntu-minus-the-DE, which I think you're trying to get at, are far too extensive to list, even if someone had a handy list. As in Arch, the package manager will bring in any and all needed dependencies.

The mini.iso is essentially a network install:  Just enough in the image to boot, create a network connection, and then start pulling down all the other bits. At one point in the procedure, you are given a chance to select from a dozen or more install options.  These range from various server configurations to full-blown setups of each of the official Ubuntu desktop flavors. (You can also not select anything at that point.)

The server image installs a basic server setup, minus a DE. 

A number of applications in the Ubuntu repositories are linked with a few Unity libraries, so those libraries will be pulled in as dependencies when they are installed, on any DE.

---

### Post by sudodus on 2014-11-15
You can test various combinations of packages (multiboot if there is space on the internal disk, or re-installing). See this list of sizes on disk and in RAM for some choices:

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

(The fact that is uses a non-pae kernel does not change the size of the system.)

---

