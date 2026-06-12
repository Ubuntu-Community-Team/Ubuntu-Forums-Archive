---
title: "X-Window System Failure on Toshiba Laptop"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by gwinston99 on 2006-02-22
I posted yesterday that I was unable to boot Ubuntu from the live CD in order partition my drive using GPARTED.  Someone responded and suggested I try the GPARTED Live CD.  I did this and it worked great.  I was able to partition my drive as desired.

Today I used a Ubuntu Install CD.  Install went fine up until the point where I was prompted to remove the CD so the system could boot into linux.

At that point I got the same problem with X-Windows.

The message says:

The X server is now disabled.  Restart GDM when it is configured correctly.

                                       <Ok>

The detail output is as follows:

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523
[email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10
13:14:36 BST 2005 i686
Build Date: 10 October 2005
     Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
     to make sure that you have the latest version.
Module Loader persent
OS Kernel: Linux version 2.6.12-9-386 (guildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10
13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,

                                       <OK>


I can get to a command prompt and login with my user login, but have no idea what to do from there.

Any help would be greatly appreciated.

Thanks,

Gregg Winston
[email]gwinston99@gmail.com[/email]

---

### Post by heimo on 2006-02-22
I guess the first thing to try would be
```
sudo dpkg-reconfigure xserver-xorg
```
which will reconfigure X window system. You may then try:

```
sudo /etc/init.d/gdm start
```

---

### Post by gwinston99 on 2006-02-22
I tried the advice given, and went through the X-Server reconfiguration several times, trying different options.  

Each time, starting GNOME Display Manager fails.

Where do I go from here.

Thanks for your help.

Gregg

---

### Post by fsck0ff on 2006-02-22
Dude, what is your laptop?
Like what kind of video card is in it? 
I had this problems with mine (satellite l20-182 with radeon xpress200m), because the ati driver doesn't support this chip, so I edited the config, changed ati driver with vesa, after that installed the fglrx driver, changed vesa to fglrx and everything works fine now :)
So the point is please tell us what is your video card :>

---

### Post by gwinston99 on 2006-02-23
I have the same Video card as in your Toshiba.

I am a relative newcomer to Linux and Ubuntu.  I have installed Ubuntu successfully on another laptop and on a desktop system.

But I will need more basic/detailed instructions if any of the config files need to be edited.

Thanks,

Gregg

---

### Post by Greg2 on 2006-02-23
[QUOTE=gwinston99]But I will need more basic/detailed instructions if any of the config files need to be edited.[/QUOTE]
Reboot in recovery mode and edit your xorg.conf with:```
 sudo nano /etc/X11/xorg.conf
``` and in the device cell where Ati driver is called, edit by adding the line:```
Option     “noaccel”
```or as fschOff has noted; replace ati with vesa if noaccel doesn’t work for your system.

Then restart the gui with:```
sudo /etc/init.d/gdm restart
``` Please note that if you’ve never used nano or pico see man nano.

Now you have a gui but no usable Ati driver... for that go here and follow the instructions:
[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)
Or go here if you want to install the latest version... and you feel comfortable with the instructions:
[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

---

### Post by gwinston99 on 2006-02-23
Success!

I reconfigured xserver-xorg again, this time choosing VESA instead of ATI, and left all of the other default settings.

I have now been able to boot all the way to the gnome desktop, get on the web with my wireless connection, and I am sending this message via Firefox.

Now I have 3 questions:

1. My sound is lousy, how do I troubleshoot this?
2. How do I install fglrx?
3. How do I upgrade to Firefox 1.5?

Thank you all very much for your help.  I am excited about getting away from M$FT.

Gregg

---

### Post by varunus on 2006-02-23
1.  What do you mean your sound is lousy?  It could be a multitude of things...

2.  fglrx can be installed with the following howto:
[http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)
Make sure to select the fglrx driver when doing the X reconfiguration recommended in that step, and don't do the libdri thing if you're on Ubuntu i386 (as opposed to Ubuntu64).

3.  Here's how to get Firefox 1.5:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
Make sure to follow the instructions carefully, or things might break.

---

