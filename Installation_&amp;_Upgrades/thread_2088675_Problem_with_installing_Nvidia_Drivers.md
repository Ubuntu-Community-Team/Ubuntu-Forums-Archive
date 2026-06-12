---
title: "Problem with installing Nvidia Drivers"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by tdgs on 2012-11-27
Hi all

I have a fresh install of kubuntu 12.10. I haven't installed anything.For some unrelated reasons I decided to install an older version of the Nvidia drivers (310.19 version was causing some problems to my system).So instead of doing a 

**sudo aptitude install nvidia-current** 

II downloaded 304.51 version from here


[http://www.nvidia.in/Download/Find.aspx?lang=en-in]("http://www.nvidia.in/Download/Find.aspx?lang=en-in")

When I tried to run the installation the first error message I got was

"You appear to be running XServer quit Xserver before installing".

So I switched consoles to tty1 and typed

**service lightdm stop**

When I tried to run the installer again I got this message

"The Nouveau kernel driver is currently in use by your system. 
The driver is incompatible an must be disabled before procceding"

So I went to 

[http://in.download.nvidia.com/XFree86/Linux-x86_64/304.51/README/index.html]("http://in.download.nvidia.com/XFree86/Linux-x86_64/304.51/README/index.html")

Which is the README file for my drivers and I found out that Nouveau is the driver my linux distribution comes shipped in. It was reversed engineer by the Nvidia drivers. Before I installed the nvidia drivers I had to disable it which seemed logic enough.

Loooking at the instructions I found out that I should blacklist the nouveau driver to prevent it from loading I had to blacklist it ( [http://in.download.nvidia.com/XFree86/Linux-x86_64/304.51/README/commonproblems.html]("http://in.download.nvidia.com/XFree86/Linux-x86_64/304.51/README/commonproblems.html"))

I edited the /etc/modprobe.d/blacklist.conf file and I added these two lines

[B]blacklist nouveau
options nouveau modeset=0[/B]

I restarted my system and again stoped the lightdm servise

**sudo service lightdm stop**

Tried to install the drivers again and... I got the same mistake. Continuing reading the README file revealed some usefulll information 

[I]"How do I prevent the X server from loading Nouveau?
	

Blacklisting Nouveau will only prevent it from being loaded automatically at boot. If an X server is started as part of the normal boot process, and that X server uses the Nouveau X driver, then the Nouveau kernel module will still be loaded. Should this happen, you will be able to unload Nouveau with `modprobe -r nouveau` after stopping the X server, as long as you have taken care to prevent it from doing a kernel modeset; however, it is probably better to just make sure that X does not load Nouveau in the first place."[/I]

So I tried to type (after I had blacklisted it ofcourse)

[B]sudo service stop lightdm
sudo modprobe -r nouveau[/B]

but I got 

**FATAL : Module Nouveau is in use.**

Which explains why I couldn't get the nvidia driver to get intalled in the first place. 

In my desperation I even tried to completely remove the nouveau driver (it was a fresh installed even if I damaged my system I could just reiinstall everything)

**sudo apt-get --purge remove xserver-xorg-video-nouveau**

I restarted my system. Surprisingly I got the login screen. I didn't bother logging in I switched to another console (tty1) and repeated the same proccess. 

[B]sudo service stop lightdm
sudo modprobe -r nouveau[/B]

only to receive again

**FATAL : Module Nouveau is in use.**
So.... any advices??

Thank you for your time

---

### Post by darkod on 2012-11-27
What if you try to select the recovery mode entry in the grub boot menu? After the recovery menu shows up, select Drop to root shell which will only open the shell as root and no GUI. So I guess it never tries to load X or nvidia modules especially if they are blacklisted.

Then you can try installing it at the command line in the shell. Note that the root shell is read-only, to remount it as RW do:
mount -o remount,rw /

---

