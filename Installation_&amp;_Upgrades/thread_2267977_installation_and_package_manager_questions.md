---
title: "installation and package manager questions"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by mattrix2 on 2015-03-05
Hi,
Complete n00b here. There is just too much choice and too much (often contradictory) information out there.
I have been recommended to install Ubuntu (or some flavour thereof), mainly because of its large repository and reliable package management. 

What is package management?
I get the impression that the package manager sorts out dependencies, gets the package(s) and works out the order in which they should be installed. The actual installation and uninstallation of a package is handled by a scripts supplied with the package.

I have been told that my hardware is marginal (<1GHz, <1GB) and that a standard intall of Ubuntu, will probably install too many packages to run properly. BUT that using the package manager I can safely uninstall any unneeded packages, or even ALL of the installed packages if I want. AND this would leave me with a working absolute minimum installation. The package manager makes sure that only unused files are deleted?

Questions:
Is all of the above correct?
What are the packages installed by the standard install?
What are the minimum / not removable files?

I am thinking I might be better off finding a minimal installation, that can use the Ubuntu repository and package manager, and adding any packages to that. Are there any good candidates for this?


PS still on installation, how is the kernel configured during installation, Best match for your hardware out of a set of precompiled kernels, or is it customized/compiled on the fly for your hardware.

---

### Post by Bucky Ball on 2015-03-05
Welcome. 

> **mattrix2 said:**
> Hi,
What is package management?
I get the impression that the package manager sorts out dependencies, gets the package(s) and works out the order in which they should be installed. The actual installation and uninstallation of a package is handled by a scripts supplied with the package.

More or less, yes. 

> **mattrix2 said:**
> I have been told that my hardware is marginal (<1GHz, <1GB) and that a standard intall of Ubuntu, will probably install too many packages to run properly. BUT that using the package manager I can safely uninstall any unneeded packages, or even ALL of the installed packages if I want. AND this would leave me with a working absolute minimum installation. The package manager makes sure that only unused files are deleted?

Lubuntu or possibly Xubuntu would be about it. You could try Ubuntu for fun, but don't know if the computing experience would be satisfactory.

You can cause some real problems and it is a never ending story trying to delete all unwanted packages. You can rip out dependencies that are shared with other apps in the process, causing chaos. Better to go the other way and use something like the minimal install. It just installs the base kernel, you install the rest (a steep learning curve, but if you're up for it, you'll find help with it here). 

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

> **mattrix2 said:**
> What are the packages installed by the standard install?
What are the minimum / not removable files?

The first part you can find with a bit of googlin'. The second, almost unanswerable. You are looking at many thousands of files and to know and list what is required is totally dependent on what you have installed. Beyond the scope of this post.

> **mattrix2 said:**
> PS still on installation, how is the kernel configured during installation, Best match for your hardware out of a set of precompiled kernels, or is it customized/compiled on the fly for your hardware.

The install will see what you have hardware-wise and install the appropriate drivers for it. No different kernels. All the drivers are in the one. Only the software required for your hardware is used. The only exception to this would be where a driver is missing from the kernel and this would generally apply to some graphics cards and wireless devices. This can generally be rectified post-install. Motherboard, RAM, hard drives, all there. 

Best bet? Download the Lubuntu [14.04 LTS ISO ]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")(supported until April 2017, 32bit version for ALL 32bit processors, AMD 64bit for ALL 64bit processors), burn a disk or USB, boot, 'Try Lubuntu'. See how you go. Dive in and have a look around. Good luck and hope that helps. ;)

---

### Post by kc1di on 2015-03-05
Hello mattrix2 and welcome to Ubuntu,

I'll try and answer your questions:

1 the Package management system  is called apt.  It does a very good job of dependency resolution and is very versatile.  The software center in Ubuntu and other Distros that use the APT package manager is a front end for the program.  you can learn more about apt[ here. ]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")

     It would be a misnomer to say that it handles package installations by a script though scripts are used.  It's a very good way to install and uninstall programs/packages on Ubuntu.  This [Tutorial]("https://help.ubuntu.com/community/AptGet/Howto") will give you more info. 

2.  Your hard ware looks to be minimal for Unity - Which is the Desktop used in the flagship Ubuntu release. It will depend more on your video card as to if it would run on that machine.  You may be better off with Mate, XFCE , KDE or LXDE.  as your desktop.  Your correct in that there are many choices in Linux and Ubuntu and that is a good thing, best way to try out each one on a Live DVD or USB stick and try each desktop version (I.E. Kubuntu for KDE, Xubuntu for xfce, Ubuntu-Mate for mate or Lubuntu for LXDE)  Remember live media won't change or add anything to you current Hard drive.  so it will not alter your current O.S.  and remember that it will be about 2x slower in a live session than if it were installed because it has to un-compress the files it's using on the fly.   You can find minimum system requirements [here.]("http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop")

3. What are the packages installed by the standard install?  -- There are so many it would be hard to list them all -- But you'll get the packages needed to run the system, create the Desktop environment (IE Unity) and browser, e-mail client some sort of text editor , office suite , Etc. enough for a complete desktop experience. 
The actual programs installed will very somewhat from Desktop to Desktop. Depending upon the choice the Developers have made when they put it together.  One of the great things about Ubuntu and it's community Derivatives is the Hugh number of programs /packages you can install , you'll find that there is a program to do just about everything you could imagine you would need to do on your Computer.  (The choice at first may seem overwhelming but again it's a good thing.)

4. the Kernel - The kernel is built and compiled by a team of developers at the Kernel project : see [Here ]("http://en.wikipedia.org/wiki/Linux_kernel")for more info.

The kernel is modified by the Ubuntu team to work well with it's Distribution.  Modules , for different Hardware drivers are added at the time of install to match your particular hardware complement.  Sometimes these will have to be changed after install depending upon your Hardware, mostly because the hardware manufacturers keep their driver code closed source.  Some hardware vendors are better that others at working with the Linux kernel.  Nvidia graphics works to provide drivers of their own for Linux but they can not installed during system install because of licensing requirements. and so if you have an nvidia card you'll have to do some work post install to get it working properly.  

I'm sure others will have more to say and may say it in a better way, but that will give you some food for thought.

Hope you decide to join the Ubuntu Gang and Linux in general.  you'll learn a lot and find many new friends here :)

---

### Post by Impavidus on 2015-03-05
> **mattrix2 said:**
> 
I have been told that my hardware is marginal (<1GHz, <1GB) and that a standard intall of Ubuntu, will probably install too many packages to run properly.

That hardware will not be capable of running a standard install of Ubuntu. But that's not because a standard install of Ubuntu installs too many packages. Extra packages only take disk space, nothing else, as long as you don't use them. Your problem is that standard Ubuntu uses a desktop environment that is too heavy for your hardware. Lubuntu is a light flavour of Ubuntu, coming with a light-weight desktop environment and some other light-weight alternatives to standard Ubuntu software. The difference between Ubuntu and Lubuntu is only in the default software, everything from Ubuntu is installable in Lubuntu too and vice versa.

---

### Post by grahammechanical on 2015-03-05
> [COLOR=#000000]The package manager makes sure that only unused files are deleted?[/COLOR]

The package manager can replace packages that are being used with upgraded versions.

 In a sense, packages removed without being upgraded are indeed packages not being used. That is not to say the they are not needed. We can, if we are not careful, remove enough "unused" packages to make the operating system unusable the next time we restart.

Which is why I never use Janitor software that allows us to "clean up" the OS. In the past, in my ignorance, I have given a Janitor type program the authority to remove needed packages. And broken the installation.

If you want a working, absolute minimum Linux computer operating system then use the Ubuntu minimum CD ISO image and go no further than installing Linux. That is as minimal as we can get. We can, if we wish, be a little or a lot less than minimal by selecting the groups of packages to be installed. We are in control but do not expect simplicity in the installation process.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Regards

---

### Post by mattrix2 on 2015-03-05
Thankyou for your thoughtful replies and warm welcome.

Sorry, [COLOR=#000000]Impavidus, I meant things like daemons running and using cpu and memory.

[/COLOR]Interesting that the kernel is one size fits all. I had expected there would be different kernels compiled for the different processor capabilities, mmx, sse etc, and maybe the typical chipsets for those processors. A one size fits all would have to be compiled for the minimum instruction set and the maximum hardware support, which would make it somewhat more demanding.

I tried Lubuntu a while back but for some reason the installation wouldn't complete. I've been assured that Ubuntu desktop is less fussy about installation conditions. Thanks for the psychocats link [COLOR=#000000]Bucky Ball, I'd seen the minimalCD link before but dismissed it as it implied that it only did a full install.

[/COLOR]And thanks [COLOR=#000000]kc1di [/COLOR][COLOR=#000000]for the tutorial. It reads as if apt can handle removing packages cleanly[/COLOR] (provided they were installed with apt?)

This machine ran XP (acceptably AFAIK) in a previous life. So I'm left wondering will I have to remove more than I leave; Build up or dig down. I have found the manifest, but is there anywhere I can get the dependency list for the packages?

---

### Post by Bucky Ball on 2015-03-05
Build up. Definately less 'accident' prone. And time consuming! Just takes more planning, but if you're just getting into it, a good adventure if you have the time. I started using minimal installs two or three years ago, by which time I'd used a lot of programs and knew what I wanted. I run a mini install on an i3, 4Gb ram machine with xfce4 desktop environment and the apps I want/need only. No bloat. ;)

The other option is to install Lubuntu on one partition and post a thread if you have issues installing, and install a minimal 'plaything' on another partition for learning and customising your ideal OS. That way you have a stable install once you have the regular Lubuntu up if you need one.

---

### Post by dino99 on 2015-03-05
Your hardware will have some hardtime to run 3d apps/system; so choose 'light' distro like 'Lubuntu/Mate' with the minimal apps installed. The mini.iso let you doing that as you wish, simply be zen and read the proposed options when they pop-up. There is a few meta-packages you might not install (or purged after installation) like Lubuntu-desktop (as meta-package, it is only a list of package names to install, not the packages themselfves), xserver-xorg-video-all, xserver-xorg-input-all. Some userfriendly apps should be installed: synaptic, localepurge (run it into a terminal: sudo localpurge)  ):P

---

### Post by Bucky Ball on 2015-03-05
If you go with a minimal install, do NOT install lubuntu-desktop or *buntu-desktop anything. Installing lubuntu-desktop in a mini install is equivalent to installing Lubuntu. (I'm unaware of the meta-package method described above, if 9d9 would like to elaborate. ;)) So if you intend to do that, just install Lubuntu to start with as you'd be defeating the purpose of a minimal install otherwise.

lubuntu-desktop will drag in ALL default apps and their dependencies, same as kubuntu-desktop would drag in Kubuntu's, also equivalent to simply installing Kubuntu to start with.

If you want the Lubuntu desktop environment, install lxde. Xubuntu DE = xfce4. You can install any app from any flavour. They are all in the same repositories (yes, install a desktop environment and Synaptic Package Manager first up).

You could start with a window manager, Synpatics and a desktop environment. First boot after a mini install takes you to a 'giant terminal'. Log in and give it something like:

```
sudo apt-get install lightdm synaptic xfce

```
... for example. You might go with a different window manager and desktop environment.

---

### Post by mattrix2 on 2015-03-05
Thanks for all the advice.

I didn't necessarily want a minimum install, I was just looking for a replacement for XP on the machine, and a friend is urging me to give  ubuntu a try.

Not doing a standard install just became necessary as it won't run well on the hardware.

But small is good .....

---

### Post by Bucky Ball on 2015-03-05
Perhaps you'd be best posting a new thread(s) regarding what is happening when you try and install Lubuntu and outlining your hardware. Perhaps we can get it sorted out and you can dive in.

---

### Post by kc1di on 2015-03-05
With your machine - give Lubuntu /mate a try -- Xfce will run but rather slow.

---

### Post by mattrix2 on 2015-03-08
Sorry, my last post wasn't worded very well.


Back on the package manager,
How does it know whats already on your computer? 
Does it scan and look for things or does it just know what it has installed, possibly by scanning scripts? 
Assuming all the dependancies are installed is it possible to manually install a package file? Will the package manager be able to see this package, and be able to uninstall it?

---

### Post by oldos2er on 2015-03-08
APT maintains lists of packages from enabled repositories that indicate whether they are installed, not installed, etc. See [https://en.wikipedia.org/wiki/Advanced_Packaging_Tool](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool) and look under the Files heading.

Manually installing a package usually means using dpkg, e.g. ```
sudo dpkg -i foo.deb
``` and you can also use dpkg with the -r option to remove it.

---

### Post by mattrix2 on 2015-03-11
hey, oldos2er,

Actually I meant downloading the package, mounting it and running the install scripts myself.

I looked at wiki, are you refferring to the 'state information', when does this get updated?

---

### Post by ian-weisser on 2015-03-11
> **mattrix2 said:**
> Actually I meant downloading the package, mounting it and running the install scripts myself.

Even if you figured out where all the pre-install, install, and post-install scripts were, and ran them properly, all you would do is install the software without telling the package manger.
You are welcome to try it, of course. It's your system.
But why mislead the package manager? Then it can't take care of dependencies and updates properly for you.


> **mattrix2 said:**
> I looked at wiki, are you refferring to the 'state information', when does this get updated?
State information gets updated by dpkg when it installs or uninstalls or otherwise changes the state.

For your previous posts, you wondered if apt was merely an application that scans your system to determine the package state.
No, it's not that at all.

Packages and dpkg/apt are like railway tracks and trains. Each is only half the system. They are designed for each other.  

dpkg  and apt are critical components of any Debian-based operating system.  They manage ALL packages, and their dependencies, and their updates for  you. Dpkg *remembers* the changes of every package state, since it is  the only application that changes the state. All other Debian/Ubuntu  package managers (Software Center, Software Updater, Synaptic, apt-get,  etc) are built on top of dpkg and apt.

---

### Post by mattrix2 on 2015-03-13
Thankyou Ian,
> **ian-weisser said:**
> 
But why mislead the package manager? Then it can't take care of dependencies and updates properly for you.

That wasn't my aim, really!, I'm just trying to work out how things work so that I can plan what I'm up to. Working with the package manager instead of against it. Your description helps a lot.
> **ian-weisser said:**
> 
State information gets updated by dpkg when it installs or uninstalls or otherwise changes the state.

Are there tools to interrogate the state information to find out exactly what is installed on the system and why, eg. as a dependency for something else? 

When you install a package, the manager tell you what dependencies it will install as well, before you commit? 
Similarly when you are removing something, does it tell you what else will need to be removed as it is dependent on what you are removing, before you commit?

---

### Post by Bucky Ball on 2015-03-13
As for removing something, if you run:

```
sudo apt-get autoremove
```

... after removal it will remove anything that is no longer required and no longer depended on by anything else (some dependencies are shared by more than one program).

---

### Post by oldos2er on 2015-03-13
> **mattrix2 said:**
> 
Are there tools to interrogate the state information to find out exactly what is installed on the system and why, eg. as a dependency for something else? 

Of course. apt-get and dpkg commands can give you this information. If you want a GUI program, try Synaptic Package Manager.

> **mattrix2 said:**
> When you install a package, the manager tell you what dependencies it will install as well, before you commit? 
Similarly when you are removing something, does it tell you what else will need to be removed as it is dependent on what you are removing, before you commit?

Yes. *sudo apt-get install -s foo* can run simulations (that's what the -s flag is for) to show you exactly what would occur. I'm not sure if any of the GUI package managers can do this, but I don't think they can.

---

