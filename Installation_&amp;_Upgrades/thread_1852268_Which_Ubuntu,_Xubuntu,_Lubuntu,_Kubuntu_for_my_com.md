---
title: "Which Ubuntu, Xubuntu, Lubuntu, Kubuntu for my computer"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by bonheur1 on 2011-09-29
I would like to install one of the several Ubuntu distributions (Ubuntu, Xubuntu, Kubuntu, Lubuntu) for use on a personal computer running Windows 7. That is I would install the Linux distribution under Oracle's VirtualBox.
 
The main hardware on my computer is:
 
Intel Pentium Dual CPU E2220 2.40 Ghz
3.49 GB of usable RAM
The graphics card, is an Intel integrated one. I don't remember which one from the top of my head. It's on an Asus mobo bought sometime in 2009.
Windows Experience Index of 3.3
 
I would dedicate about 32 GB of hard disk for the Linux distro plus anywhere between 1 GB and 1.5 GB or RAM (that'd depend on your advice).
 
Thank you in advance! :)

---

### Post by LinuxFan999 on 2011-09-29
Since you are installing Linux on a Virtual machine, you should use ether Xubuntu or Lubuntu, because Ubuntu and Kubuntu will run very slow under Virtualbox, especially on a machine like your's. Don't forget to enable 3D acceleration and install the guest additions.

---

### Post by bonheur1 on 2011-09-29
That was fast! Thank you! :-)
 
Could you please help me choose between Xubuntu and Lubuntu?
 
Also, should I run the Ubuntu-flavor of Xfce / LXDE or a completely different Linux distribution running any of those desktop environments?
 
I'll be using the distro for web browsing, email, instant messaging plus a bit of coding in C and Python (IDLE, Vim and Gedit or similar). I'll be doing all my office tasks on the host environment so no need for LibreOffice/Abiword/Gnumeric/Gimp, but I could certainly use some basic features.
 
Eventually, I'd appreciate some tips on how to properly set up VirtualBox. How much RAM should I allocated for the guest distro? How much video memory? etc.
 
Thank you in advance.

---

### Post by LinuxFan999 on 2011-09-30
Lubuntu would be the best out of those two for usage on a virtual machine. The Ubuntu flavor of LXDE would be the best. the HTML version of the Virtualbox user manual can be found here: [https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)
You should allocate 1.5 GB of RAM, 32 MB of video ram, enable 3D acceleration, and allocate at least 15 GB of hard disk space (you can allocate 32 GB if you want to).

---

### Post by bonheur1 on 2011-09-30
Thank you! :-)
 
Lubuntu it will be.
 
Do I have to be aware of any limitations of the Lubuntu distribution compared to the Xubuntu one? I was able to "play" with it for a limited time period so I've got a slight idea what I may expect out of it for comparison sakes.

---

### Post by MG&amp;TL on 2011-09-30
Because they are based around the same terminal/packaging system/kernel, you can in theory do anything with Lubuntu that you can with anything else. It's just a personal interface choice, and the heavier desktops have more eye-candy.

And lubuntu has less (GUI) options for customization, whereas I genuinely haven't found all of the kubuntu ones yet. That said, you can change pretty much anything via the command-line, whichever desktop you run.

---

### Post by MG&amp;TL on 2011-09-30
Or you could set lubuntu as the main one, and setup a 3GB one for Xubuntu (as a test)

---

### Post by bonheur1 on 2011-09-30
Thank you for your input! That's certainly helpful.
 
As for eye-candy I like Xfce, but I guess I should go with Lubuntu if it is significantly faster on a VirtualBox machine. As long as it doesn't have any limitations over the other distributions I will be fine.

---

### Post by MG&amp;TL on 2011-09-30
> **LinuxFan999 said:**
> 
You should allocate 1.5 GB of RAM, 32 MB of video ram, enable 3D acceleration, and allocate at least 15 GB of hard disk space (you can allocate 32 GB if you want to).

1.5 GB may be overkill. Whatever you can spare, really.

---

### Post by MG&amp;TL on 2011-09-30
> **bonheur1 said:**
> As long as it doesn't have any limitations over the other distributions I will be fine.

You might have to use a command-line more often than other desktops. As long as you are happy with that. 

Any other distribution that uses LXDE will be equally fine, but the packaging system for ubuntu (and derivatives) is famously easy-to-use, while others can be less user-friendly, or even involve manually compiling.

---

### Post by MAFoElffen on 2011-09-30
I "test" alpha and beta distro's in VirtualBox... I do most testing in native installs, but... This is what has worked best for me on VirtualBox memory allocations when setting up virtual machines:

Look at the distribution's system requirements...  There should be a minimum and a recommended listed.  I usually set it at the recommended amount.

I used to set "higher" and it really didn't work out as well.  What was happening is that I had several virtual machines going and things running in background... and it was crawling as it had to swap to disk.  It works out as a balancing act.

---

### Post by bonheur1 on 2011-09-30
> **MG&TL said:**
> You might have to use a command-line more often than other desktops. As long as you are happy with that. 
 
Any other distribution that uses LXDE will be equally fine, but the packaging system for ubuntu (and derivatives) is famously easy-to-use, while others can be less user-friendly, or even involve manually compiling.
 
Why would I have to go to the command line more often? I hope I don't have to work out all of the software dependencies on my own. I preffer to install packages from the GUI if that's what you meant.
 
>  
lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. The lubuntu team aims to earn official endorsement from Canonical. 

 
Would that be an issue somehow?

---

### Post by MG&amp;TL on 2011-10-01
No, the dependencies will be fine. I was thinking more along the lines of if you wanted to change the WM, or change the little start icon.

Anything basic would be very easy to do via GUI.

As of 11.10, Lubuntu is endorsed by Canonical, so no. :)

---

