---
title: "WILL PAY for troubleshooting in DFW, US area"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by dell49 on 2012-11-09
Well, what I always dreaded: attempted/half succeeded with upgrade to 12.10 on my Toshiba Portege (partitioned) laptop EXCEPT libqtgui4:i386 and libtiff4:i386 were corrupted coming down. Now, Software Update won't work and I get messages about bad packages.

I know that I could rectify this by starting over entirely with a new install of 12.10, but I would like to keep my files which (I presume) would be lost by doing that.

So, are there any talented people in the Dallas - Ft. Worth area that I could bring the laptop to, so this problem can be rectified? Or is this unfixable, and I should just write off my files and reinstall the operating system? 

And what is an appropriate stipend for this: $50/hour or higher?

Thanks in advance for any assistance or advice.

---

### Post by uRock on 2012-11-09
If you decide that you need to do a clean install, then you can use a live image to boot the system and back up your data.

---

### Post by stinkeye on 2012-11-09
Try your Fort Worth Linux Users Group (FWLUG).
[**_[COLOR="DarkRed"]http://www.fwlug.org/[/COLOR]_**]("http://www.fwlug.org/")

---

### Post by ibjsb4 on 2012-11-09
Guess you could try contacting the Dallas team.

[https://launchpad.net/~ubuntu-dallas](https://launchpad.net/~ubuntu-dallas)

Why don't you let us have a look to see just how bad off you are?

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And post any errors you get.

---

### Post by dell49 on 2012-11-10
No error statements when I did that. But Software Updater finds and tries to download the missing/corrupted JBIG kit libraries and the Tag Image File Format libraries, then requires authentication, then crashes. I tried to copy the crash report details, but can't.

---

### Post by Old_Grey_Wolf on 2012-11-10
Try running update manager from the command line. Enter the command ```
gksudo update-manager
``` in a terminal (key combo Ctrl+Alt+t). Enter your password. Then see if you can check for updates and install them.

---

### Post by dell49 on 2012-11-10
Thanks! Tried that. Still got "The package system is broken" message. And can't report the error either, asks for password and then, when that's entered, it crashes.

---

### Post by ibjsb4 on 2012-11-10
In terminal:

sudo apt-get -f install

---

### Post by dell49 on 2012-11-11
ibjsb4 particularly:

Thanks a ton. Now working just as it should!! And no more big red circle! Could NOT have done this without this community, and the help provided. Put this one in the "solved" category.

---

### Post by Old_Grey_Wolf on 2012-11-11
dell49,

I am glad you got it sorted out.

---

