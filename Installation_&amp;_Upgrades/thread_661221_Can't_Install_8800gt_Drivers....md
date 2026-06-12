---
title: "Can't Install 8800gt Drivers...?"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by climburr on 2008-01-07
I recently installed Ubuntu, but as far as I know, i'm without drivers for my nvidia 8800gt video card.
I downloaded Envy, and I can't install it. I also downloaded the drivers direct from nvidia, but it says "could not open the file /home/jack/desktop/nvidia..ux-x86-169.07-pkg1.run"
"gedit has not been able to detect the character coding"
Any ideas?
Also, if i installed ubuntu on my entire harddrive and want to partition my hd now, how should I do it? Thanks a ton!

---

### Post by Steveway on 2008-01-07
Did you try the restricted-driver manager?
That should be your first point to look for installing those propietary closed-source drivers.

---

### Post by climburr on 2008-01-07
It says my hardware doesnt need any restricited drivers.

---

### Post by RebounD11 on 2008-01-07
> **climburr said:**
>  "could not open the file /home/jack/desktop/nvidia..ux-x86-169.07-pkg1.run"
"gedit has not been able to detect the character coding"
Any ideas?
Also, if i installed ubuntu on my entire harddrive and want to partition my hd now, how should I do it? Thanks a ton!

1. Why would you try to open the installer with gedit? Try like this

```

cd /home/[your username]/Desktop/
su
{now enter root password}

./nvidia..ux-x86-169.07-pkg1.run

or 

sh nvidia..ux-x86-169.07-pkg1.run

```

If you haven't updated the kernel yet, or didn't install any other drivers I recommend the restricted drivers, if those don't work use envy to remove them and try again with envy to install them. I would resort to a manual install if everything fails, especially if you're new-ish to Ubuntu. Be sure in the last case to follow the instructions on the nvidia page for installation and configuration, you might learn sth useful :)

2. Try GParted for partitioning... it's a great tool. But be careful you can do serious damage to your current installation and loose data if you get sth wrong, so double check and/or ask around if you don't understand sth.
You can redistribute your free space with this program to create new partitions and resize old ones. Again be careful with it.

I hope this helps and I hope you don't feel that I am making fun of you or that I think you're incapable of doing stuff right :D... I really am trying to help (my girlfriend said the tone was a "little" like looking down on you, and that was not intended).

EDIT: I didn't see your last post just know :D

---

### Post by climburr on 2008-01-07
Alright I'll try it, and i'll be sure to be careful. I didnt think you were looking down on me, just giving helpful advice. Thanks a ton, ill tell you how it goes.

---

### Post by climburr on 2008-01-07
I dont quite understand (i'm new to ubuntu) what you mean when you say to use that code. how do i use? it the terminal? also, how would i get or use restricted driverS? thanks!

---

### Post by punkybouy on 2008-01-07
Automatix used to install Nvidia drivers.  Go to getautomatix.com and install the right version for your setup.  Once installed you may find that it will install your drivers.

---

### Post by papatrpt89 on 2008-01-11
Ho boy.  Here we go.

OK, so.  I just built a new PC with my friend, its quite nice, Intel Quad-core 2.4 gigahertz processor, 4 gigs 800mhz ram, and, most pertinently, two Nvidia 8800GT cards running in SLI.  We installed a copy of XP, and SLI is working fine there.

From looking around the net, the only way to get these drivers up and running is a manual install.  Envy doesn't seem to support them yet, and the restricted-manager in Ubuntu doesn't either.

**[SIZE=3]Step-by-step guide[/SIZE]**

1. Download the latest drivers from Nvidia (Nvidia.com, click download drivers, GeForce 8 series, blah blah blah).  The current driver as of this writing is version [169.07]("http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run")

2. Be sure you have the necessary packages installed:
```
sudo apt-get install build-essential gcc-3.3-base
```3. Hit Control+Alt+F1, to kill the GUI and log into a shell.
  
4. Issue the command sudo /etc/init.d/gdm stop.

5. Change to the directory where you download the driver installation file with the cd command.  Probably will look something like:
```
cd /home/*username*/Desktop
```6. Run the installer for the driver.
```
sudo sh NVIDIA-Linux-x86-169.07.pkg1.run
```7. Follow the directions provided by the installer package, be sure to compile a kernel module for the kernel.

8. Once it is successfully finished, type sudo reboot.

9. Hopefully, before your login screen, you see the Nvidia logo flash on your screen.  If so, everything should have worked!  Enabling compiz is also a good test.

**[SIZE=3]Notes:[/SIZE]**[LIST]
[*] I know that Nvidia provides some kind of a configuration tool for your X configuration file, separate and apart from the installer file.  I didn't need to use it myself.
[*]When using this driver, the fans on the graphics cards will remain constantly on.  The cards don't seem to run hot, at all.  It is just a limitation of this driver.
[*]Following these steps worked great for me, running two 8800GTs in SLI, though I believe the steps are identical for a single card.
[*]I ran the steps from a clean install of Ubuntu 7.10, though the steps here should work on any Ubuntu system, that hasn't had much mucking about in the X configuration since install.
[*]Some people have had some NASTY problems installing this driver.  [This]("http://ubuntuforums.org/editpost.php?do=editpost&postid=4119312") thread has some tips that worked for some people.[/LIST]I mostly organized a post from or1on, located at [http://ubuntuforums.org/showthread.php?p=4104803](http://ubuntuforums.org/showthread.php?p=4104803)

Credit to him, and good luck!  Please post back with your experiences.

---

