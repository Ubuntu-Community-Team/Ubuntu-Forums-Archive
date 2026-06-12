---
title: "Should I Install Kubuntu Desktop in Gutsy?"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by pushin50 on 2008-01-29
I'm a Newb but learning quickly.

I am using ubuntu for three basic things: 1) openoffice suite; 2) recording of old LPs to audio CD and other digital files formats (mp3); and 3) editing home video to create new video DVDs. This computer also functions as a print server.

I'm using SpinItAgain in WINE to record LPs - I like the simplicity of that app.

For video, I think a combination of kdenLive, dvAuthor and KB3 are going to do the job for me - just downloaded them last night.

The issue I'm having is that the windows for the kde apps listed above are exceeding the desktop space in my Gutsy (Gnome?) environment. Also, font sizes are not adjusted per my Preferences/Appearance settings.

The question is, can I fix this (and generally optimize performance of  the kde apps) by installing kubuntu desktop? Second question is, how much grief will I cause myself by installing kubuntu-desktop? Is this essentially installation of an app within ubuntu or is it more like adoption of a new OS? Is the desktop a much more complex environment than gnome? My non-geek wife uses this PC as well and I'm running only ubuntu (no Windows). GUI needs to be friendly and simple.

Is this fairly low risk and worth doing?

Thanks for your help.

---

### Post by mapes12 on 2008-01-29
Hi

I think you're asking if you can run KDE instead of the default Gnome in Ubuntu 7.10.

If that is what you are looking to experiment with then what I would do is to install Kbuntu onto your machine in a seperate partion. Google Gparted to download and burn the partioning resizing application (use it to shrink the size of your current partition and create some free sapce, say about 4GB min). It's aLive CD and quite easy to use (I used it today to do a similar task). Then burn the Kbuntu iso to a  disk and boot into it on your machine.

You will need to read the installation screens carefully so that Grub is reconfigured to make the machine dual bootable into both distro's and not trash your current installation.

Mark

---

### Post by DMK62 on 2008-01-29
Hi

Are you thinking about the kubuntu-desktop package for Ubuntu ? A good site for instructions on installing it.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

My personal preference is having them installed separately. The easiest method as well as the one not requiring major reconfiguration of your system is the kubuntu desktop package. See the pros and cons listed at the link above. Besides the cluttered menus and other small issues I have found that when installing some of the plugins for kde apps they do not get installed properly.

Dale

Although almost all apps written for kde and gnome will work in either environment and are generally faster in their native environment. When opening a kde app like kopete in gnome it takes extra time as extra libraries etc need to be loaded and on exit you may get errors or system messages. Although you can customize Gnome and make it as complex as you want KDE offers you an almost endless set of options. Choosing between ubuntu and kubuntu at login is easy as all you have to do is select the session type. From my own experience I found things work better when you use gdm as the default when prompted during the install ( it can be changed later ). If the menus are too cluttered you can remove entries using the menu editors in ubuntu and kubuntu. There are also scripts out there to clean them up but I have not tried them or know how reliable they are to use.

---

### Post by Zeroangel on 2008-01-29
From my experience there are no major issues here. In kubuntu I simply install the ubuntu-desktop package and in ubuntu I install the kubuntu-desktop package.

Each one comes with its own set of apps.

The largest issue you will encounter is having a few of the KDE apps show up in your GNOME applications menus. With kubuntu it is even a bigger problem since a LOT of the gnome-administrative applets will show up as individual programs in the KDE programs menu tending to clutter that menu up a lot.

After installing kubuntu desktop and booting into into KDE is clean up the Kmenu (the programs menu) -- a good rule of thumb for that is if the app doesnt have an icon then its a GNOME administrative app and should be moved into a subfolder titled 'GNOME apps' or something similar so you dont get them confused with actual programs.

Also if, when installing Kubuntu desktop, you are presented with the option to use KDM or GDM as your login manager, you should stick with GDM since that is your default login manager for Ubuntu.

---

### Post by pushin50 on 2008-01-29
Thanks Folks!

While I can handle the partitioning suggestion, really the only thing I need to address is the window sizing issue on the desktop.Otherwise, I'm totally happy with how gutsy is working right now. For that reason, I'm going to install the kubuntu-desktop now that I have some comfort I won't screw up the whole world.

Appreciate the very helpful guidance.

Chris

---

