---
title: "[SOLVED] No display after booting"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by chambois on 2007-11-14
I have just recently installed ubuntu 7.10 amd64 and am having difficulty with my display.  I had to install via the alternate CD as I was having a similar problem with the Live CD, that being a blank screen after the ubuntu loading screen once the progress bar had finsihed.  The sound is still working (so I guess everything else installed properly), I can hear the little drum beat prompting for the user login at what I pressume is the startup screen.  When I tried the live CD it still didn't work in 'Safe Graphics' mode. 

  I am running a dual boot with XP.  I have downloaded the linux driver for my graphics card but I have no idea how to access and then install that file from the linux command line given the file is stored on the XP ntfs file system.

  I have beginners and limited experience with Linux, only knowing a few command line operations.

  My system is as follows:
CPU: AMD athlon XP+3000 (64bit, 939)
RAM: 1GB
HDD: 250 (total), 150 (ext3 partition), 100 (ntfs partition)
Video: nVidia 6600GT (Gigabyte GV-3D1 - SLI on one card), 256MB GDDR3 (128 shared), DVI
MOBO: Gigabyte nForce 4 GA-K8NXP-SLI

Any help would be greately appreciated, I've been wanting to try Ubuntu for ages!

---

### Post by IF-Rit on 2007-11-14
how long you wait???
maybe take 10 minutes....

But, if you can't boot from LiveCD maybe your RAM is not enough...
sorry, if i can't solve your problem

---

### Post by chambois on 2007-11-14
It doesn't seem to matter how long I wait.  I would have thought that 1GB of RAM would surely be enough for Ubuntu Live CD, if not at least when it is installed (where the minimun req. is 256MB i think).  

Is there any way I can play around with a config file of some sort before or during  booting so I can get some sort of display working?  Or how I would go about installing the linux driver for my nVidia card?

---

### Post by chambois on 2007-11-14
update:  I found this page which looked promising [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  and a follow on link [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/82312](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/82312) .  I tried editing the xorg.conf file, adding in the suggested 'Option "UseDisplayDevice" "dfp", and 'Option "ConnectedMonitor" "dfp, crt, tv" as well as trying the display through the VGA cable (my card has a DVI and VGA output) but nothing works - I'm still stuck with a blank screen and the login sounds.  

I was able to mount the windows partition and access the nvidia propriatry driver, but I couldn't install it as it said 'no matching precompiled kernel interface found' and I didn't have the correct headers installed - what they are I don't know.

If ubuntu wants to make some headway in the desktop market they are going to have to overcome issues like this.  If I were a beginner, novice or a casual user I would have given up long ago, im getting tired of rebooting and wasting time.

Any help would be apppreciated.

---

### Post by chambois on 2007-11-15
I have spent all day trying to get the display working to no avail.  Here is a list of the things I have attempted:

Installed latest nVidia driver, v. NVIDIA-Linux-x86_64-100.14.19-pkg2.run
Result: after the initial boot screen with the organge progress bar dispappears, the screen flashes twice at 1 second intervals between the console and a blank screen, then stays blank.  With this result there is no sound of the drum beat.

Installed previous nVidia driver, v NVIDIA-Linux-x86_64-100.14.03-pkg2.run
Result: same as above.

Tried configuring nVidia driver, using "sudo nvidia-settings"
Result: output "GtK WARNING **: cannot open display: "

Modified xorg.conf (see attached xorg.conf files)
-added 'Options    "UseDisplayDevice"   "dfp"
-added 'Options    "ConnectedMonitor"   "dfp"
-changed the 'BusID' under 'Section Device' to "PCI:5:0:0" as I read in a thread somewhere that linux has a habit of using the second GPU in an SLI system instead of the first, 
Result: When I use the generic driver for the video card, the screen just goes blank after loading and the drum beat sounds.

Tried restarting Xserver (using CTRL-ALT-BACKSPACE)
Result: same as above depending on driver respectively (blank screen with sound for generic driver, flashing screen and no sound for nVidia driver)

I'm running out of options as far as my experience can take me.  My patience is starting to wain too as I've spent all day and night getting this far.  Please help if you can, don't force me back to Windows :(

---

### Post by chambois on 2007-11-15
Problem Solved!!!

I am writing this message from firefox in Ubuntu!  I finally got it working :)  I made two changes to the xorg.conf file that I think made all the difference.  They were:

Changed the BusID to "**PCI:5:0:0**" after running '**lspci**' at the command prompt, my video card came up twice with the two addresses 4:00.0 and 5:00.0 .

Changed the display driver to "**vesa**" (i set this option using the guided xserver setup -> "**sudo dpkg-reconfigure xserver-xorg**"

The last couple of threads I found on the net regarding problems with the GV-3D1 were implying that there was no solution for this rare card (two GPU's in SLI on one card) and I was starting to worry I'd have to wait until my next hardware upgrade to try Ubuntu.   

(See the xorg.conf attached.)

Now I can kiss M$ goodbye forever! (providing I can run my games with wine)  Time to reformat the ntfs partition.  I'm loving the gnome visuals, everything is nice and smooth compared to XP.  Hope this helps anyone else out there with a GV-3D1 or an SLI setup.

---

