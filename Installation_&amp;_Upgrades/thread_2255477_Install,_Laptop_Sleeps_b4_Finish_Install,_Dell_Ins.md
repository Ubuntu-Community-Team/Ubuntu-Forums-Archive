---
title: "Install, Laptop Sleeps b4 Finish Install, Dell Inspiron B130"
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by thenox on 2014-12-05
**Issue **  
Trying to install Xubuntu 14.04 but because computer is slow/old, install takes so long that the screen goes to sleep, followed eventually by the hdd. 

**Tried So Far  **
- Moving touchpad every few minutes. Cursor doesn't move. Cursor appears frozen due to all computer resources involved with copying files/installing.
- Tried installing Kubuntu 14.04, Ubuntu 14.04, OpenSuse 14, OpenSuse 12, and Ubuntu 9.04. I can get Ubuntu 9.04 to install since it is so much quicker and less resource-intensive (or at least that's my theory). 
But computer runs Ubuntu 9 super slow (I'm assuming because Unity desktop is pretty resource-intensive, or so I've heard.) Hence, why I'm trying for XFCE.
- I've gone through the BIOS looking for any power or sleep settings but have found nothing that seems to even remotely relate to the issue. 
- Laptop is always plugged into power source (and a good surge protector) when doing install
- I've been searching online, and reading through posts but haven't found an answer. Apologies if this is a dupe post. (I've found threads and net searches with similar issues, but nothing that solved my problem yet.) 

**Machine**
Dell Inspiron B130 laptop (7-8 yrs old)
Celeron M processor, 1.6Ghz 
1GB RAM
40GB hdd

**Solution I'm Seeking**
To be able to install Xubuntu, either 14.x or no earlier that 12.x. XFCE seems less resource-intensive than Unity, and I like it a bit better than the other desktops. XFCE runs much quicker than Unity or KDE when I test it on my desktop computer, which is much faster than laptop. (Quad-core, 4GB RAM.)
Also want to install OpenOffice.
Laptop will be used for writing, internet access would be nice for research, but not essential. 
Also need sound and video.

Any help is much appreciated, if you happen to have the time to reply. Thank you.

---

### Post by ajgreeny on 2014-12-05
If you like Xubuntu and it runs OK on that machine, you may find that you like Lubuntu even more.  It uses LXDE, an even lighter weight desktop than XFCE.

Alternatively you could try using the MinimalCD-iso to install, as it will do everything from a command line, or using ncurses graphics without booting to a live desktop, which is what I assume you are using at the moment.
[Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by thenox on 2014-12-05
Hi ajgreeny,

Thanks for your reply. I might have to check out LXDE. I didn't know it was even more light weight than XFCE.
Would Lubuntu 14 be quicker to install than Xubuntu? 

What is ncurses graphics?

I would need a GUI for install. And I can't get the laptop to recognize the network hdw to be able to use an internet connection. I figure once I get the OS installed I can putz with getting all the hdw detected. 

Thanks.

---

### Post by ajgreeny on 2014-12-05
ncurses is the simple graphic output you get in a terminal such as this google search
[https://www.google.co.uk/search?q=ncurses+screenshots&ie=UTF-8&tbm=isch](https://www.google.co.uk/search?q=ncurses+screenshots&ie=UTF-8&tbm=isch)
or also if you use command **alsamixer** in terminal.

Lubuntu may install faster than Xubuntu, but on my machine both are fast, installing in about 10 mins.  I never install updates or third party packages with the OS, which speeds things up very much, and I suggest you do not do so, as it really slows down the whole procedure.

If you can't get a network easily it is going to be very difficult to use the minimal install CD, as it needs to download the GUI part of the OS while installing, not from the DVD or USB.

---

### Post by grahammechanical on 2014-12-05
You do not say what graphic adapter you have. Does it have its own memory or is it sharing system RAM?

The Unity desktop is not that resource-hungry. I am using it on a machine with 1GB of RAM but it does have an Intel Core2 Duo 2.40 GHz CPU and a graphic adapter with 1 GB of its own memory. And the graphic adapter is capable of doing hardware accelerated 3D video rendering which is needed if we are to run Unity and KDE, I believe. If your graphic adapter does not have the capability to run Unity, then you maybe disappointed with its video playback performance. Especially if the internet connection is not that fast either.

Oh, by the way, I do not remember Ubuntu 9.04 having the Unity user interface. Ubuntu did not get Unity until 11.04, if I remember correctly. So, if Ubuntu 9.04 is running slow, then it is not Unity to blame. but the computer hardware.

> [COLOR=#252525][FONT=sans-serif]Ubuntu founder [/FONT][/COLOR][Mark Shuttleworth]("http://en.wikipedia.org/wiki/Mark_Shuttleworth")[COLOR=#252525][FONT=sans-serif] cited philosophical differences with the GNOME team over the user experience to explain why Ubuntu would use Unity as the default user interface instead of [/FONT][/COLOR][GNOME Shell]("http://en.wikipedia.org/wiki/GNOME_Shell")[COLOR=#252525][FONT=sans-serif], beginning April 2011, with[/FONT][/COLOR][Ubuntu 11.04 (Natty Narwhal)]("http://en.wikipedia.org/wiki/Ubuntu_11.04_Natty_Narwhal")[COLOR=#252525][FONT=sans-serif].[/FONT][/COLOR][SUP][[32]]("http://en.wikipedia.org/wiki/Unity_%28user_interface%29#cite_note-CanonicalSplits-32")[/SUP]

[http://en.wikipedia.org/wiki/Unity_%28user_interface%29](http://en.wikipedia.org/wiki/Unity_%28user_interface%29)

Regards.

---

### Post by thenox on 2014-12-07
grahammechanical,
The graphics adapter, to my knowledge, is using  system RAM. The machine is quite old. If it does have it's own memory,  I'm sure it isn't any more than 256MB. It's a 7+ year old, budget  laptop.

Thanks for the info about Unity. Ubuntu 9.04 looked similar to Unity, so I just assumed it was. Good to know. 

I'm going to try putting an .iso image onto a USB stick, and see if I can boot/install from that. 

Regarding  the laptop going to sleep, is this a standard feature of laptops or  PC's (similar to how holding the power button on any machine eventually  shuts if off)? I haven't used another laptop for years so I don't have a  comparison.

Thanks.

---

### Post by thenox on 2014-12-07
Update: USB idea didn't work. Even if I go into the one-time boot menu, and tell it to boot from the USB, it just boots from the harddrive every time.

---

### Post by Darth Riker on 2014-12-07
Just a question - did you follow the steps outlined here: [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640) (considering the age of your laptop - do you need to use the forcepae flag?) and here: [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

Personally, since I was using a Windows machine to make the bootable USB  drive, when loading just one iso to a usb I used the method outlined  here make the USB drive: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) 

I have a Dell Inspiron 8600 and, while I haven't yet installed Xubuntu on it, I have managed to load it from a live USB (using the forcepae flag).

---

### Post by thenox on 2014-12-08
> **Darth Riker said:**
> Just a question - did you follow the steps outlined here: [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640) (considering the age of your laptop - do you need to use the forcepae flag?) and here: [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

Personally, since I was using a Windows machine to make the bootable USB  drive, when loading just one iso to a usb I used the method outlined  here make the USB drive: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) 

I have a Dell Inspiron 8600 and, while I haven't yet installed Xubuntu on it, I have managed to load it from a live USB (using the forcepae flag).



Thanks, Darth. I hadn't come across those links. I'll give them a shot. I think I put the single ISO file on the USB via Xubuntu, on my desktop computer. But I just copy/pasted. So that could also be an issue. But I remember the laptop booting from USB when I had used Linux Live USB Creator. [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
Maybe that could work, as well.

I'll see if that "forcepae" option works first. 

Have you ever heard of other laptops doing this - just going to sleep/suspend during an install, with no applicable options in the BIOS? It seems there's no place where I can tell it, "Stay awake, fool." 

Thanks.

---

### Post by Darth Riker on 2014-12-08
> **thenox said:**
> Thanks, Darth. I hadn't come across those links. I'll give them a shot. I think I put the single ISO file on the USB via Xubuntu, on my desktop computer. But I just copy/pasted. So that could also be an issue. But I remember the laptop booting from USB when I had used Linux Live USB Creator. [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
Maybe that could work, as well.


You're welcome. I, myself, and still very much a rookie when it comes to linux so I'm just sharing what I found useful.

Linux Live USB Creator should work as well. There are a few tools out there that you can try (UNetbootin being another popular one).

But yes - if you just copy/pasted the iso to the usb then that won't work. You need to use one of the tools to create a live USB.

> I'll see if that "forcepae" option works first.

They way you can find out if you need to use this is by first creating a live USB with Xubuntu 14.04.1 and, when then boot menu comes up, select the option to "Try ...". If it comes back with a PAE message then you will need to use the forcepae flag.

> Have you ever heard of other laptops doing this - just going to sleep/suspend during an install, with no applicable options in the BIOS? It seems there's no place where I can tell it, "Stay awake, fool." 

Thanks.

I can't say I have heard of this situation. Seems very odd to me.

Just to note: I managed to successfully install Xubuntu 14.04.1 to my Dell Inspiron 8600 with no issues at all (dual booting with Windows XP SP3 at this stage).

Also - it might be worth casting your eye over the page here: [http://xubuntu.org/getxubuntu/requirements/](http://xubuntu.org/getxubuntu/requirements/) (references to Desktop/Live DVD would also include the Live USB):

> 
Minimum system requirements

To install or try Xubuntu within the Desktop/Live DVD, you need 256 MB of memory, if you are using the Minimal CD, which uses the non-graphical Debian Installer and downloads packages as you install, you need 128 MB of memory.

Once installed, you should have at least 512 MB of memory.

When you install Xubuntu from the Desktop CD, you need 6.1 GB of free space on your hard disk. The Minimal CD requires you to have 2 GB of free space on your hard disk.

Perhaps you may need to use the Minimal CD installation method instead (as outlined at the bottom of this page [http://xubuntu.org/getxubuntu/):](http://xubuntu.org/getxubuntu/):)

> 
Minimal CD

If you absolutely must use a CD to install your system, and you&#8217;re able to download updates while doing an install, we recommend using the Minimal CD, which is tiny and easily fits on a CD. It uses the text-based alternate installer, which is better for older hardware.

During the installation, one of the options will be the package sets: select &#8220;Xubuntu Desktop&#8221; among them.
You can read more about the Minimal CD installation and download the appropriate ISO(s) from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I hope that this helps you and that it works for you in the end.

---

### Post by thenox on 2014-12-09
Update: Well, I used the Linux Live USB to make a Live USB, put Xubuntu 14.04 on. The only difference was the mouse didn't freeze, and the screen didn't go blank, but I couldn't get the install to progress. It just sat on the first screen of the install, for several hours. 

I think I will try making a live USB with Lubuntu 10.04. Hopefully, that should install quicker (Ubuntu 9.04 goes pretty quick so it is what I'm running on the laptop right now). 
Assuming the Lubuntu install works, hopefully the performance will be a little better since I'll be running LXDE. We'll see if that works.

Thanks.

---

### Post by mörgæs on 2014-12-09
Old and abandoned software like 10.04 is a security risk. Did you try the minimal install which was recommended four days ago?

---

