---
title: "[SOLVED] GeForce 8400 GS Video card, restricted drivers, ubuntu 7.10-server"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by freymann on 2007-12-20
I'm new to ubuntu, and am pretty pleased, but there are a couple items that are really annoying.

-for the life of me I can't get the nVidia video drivers to work
-I'm running in circles with the restricted driver thang

I came from FreeBSD, then a month in PC-BSD, and after buying new hardware, FreeBSD doesn't like it, so I'm trying ubuntu, with fairly good results.

Why is so bloody difficult to get a proper video driver to work??

After breaking my setup earlier today and fixing it (simply by copying back my good working copy of xorg.conf) I gave up but played some more this afternoon. I researched the forums, read lots of things about unable to use desktop effects, unable to use nVidia video drivers, new kernels creating no sound, etc.

I fixed up some grub files. I removed beryl. I cleaned up my software source file. I removed anything to do with restricted drivers and nvidia drivers other than 1 that I thought was necessary.

I decided to try this walk through:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

(it's hard to find an exact walk through for ubuntu 7.10-server by the way)

Method 1 seems like a logical choice.

So... here's how it went:

uname -r -> 2.6.22-14-server

sudo apt-get install linux-server

sudo apt-get install nvidia-glx

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nvidia-xconfig

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
where the file was empty, but I pasted in:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;

and saved it.

I log out or restart...

From here various things happened, but in the end, it didn't work.

I believe somewhere around this point I did:

sudo nvidia-glx-config enable

Reboot.

I either get dropped back to the terminal screen with messages I don't understand about

/dev/disk/by-uuid/ea987cba-921d-4741-a108-15dcc31a181

and a login prompt

and other "junk"

which eventually produces a login screen in 800x600 mode.

I can log back in, copy back my good working xorg.conf file, reboot, and I'm back (mind you it took me a while to be comfortable with this).

I can go to System>Administation>Screens and Graphics and play all I want, but it never "saves" what I select. Strange.

At one point, I logged in and got my 1280x1024 screen (or was 1600x1200?) but it was blurry and had 5 of everything and I was unable to read and understand what was on the screen (meaning you sure as heck aren't going to configure anything in this mode).

I ran through 

sudo dpkg-reconfigure xserver-xorg

two or three times. I compared it again my working copy. I manually edited the virtual line from 1600x1200 to 1280x1024. Nothing worked.

So I have this nice new computer:

Intel Pentium D 925 Processor, Dual-Core
2GB Ram
EVGA nForce 650i Ultar (T1 version) Socket 775 ATX Motherboard
EVGA GeForce 8400 GS Video Card, 256MB DDR2 Memory with PCI Express, DVI, VGA, TV Out
250GB Sata HD
SATA DVD-Burner

It runs great. I have a 1280x1024 screen. But somehow I feel like I have a racing car that can't get out of 2nd gear.

Do I have to sit back and wait for the "latest kernel" to include better support for my video card? (I assume that's correct Linux talk).

---

### Post by mellowd on 2007-12-20
Have you tried envy yet? It should autoinstall the driver correctly.

btw, why are you running a gui on server?

---

### Post by freymann on 2007-12-20
> **mellowd said:**
> Have you tried envy yet? It should autoinstall the driver correctly.

btw, why are you running a gui on server?

 No, I have a page bookmarked that talks about envy. Perhaps tomorrow when I'm in the mood to break things again I'll give that a go.

 I selected "server" because of the LAMP feature. Those are my absolute must have's. This is a work station for me to program, debug and test on. It's not a server out there doing things, it's just my own home personal workstation.

 SInce I was new to ubuntu, I wanted to ensure those programs got installed correctly, and Server has an option to do that.

---

### Post by mellowd on 2007-12-20
I see.

I've only used envy once and that's when I was testing an install of Mint (an ubuntu derivative) Worked a charm to get my 8800GT installed. Never been easier.

---

### Post by freymann on 2007-12-20
> **mellowd said:**
> I see.

I've only used envy once and that's when I was testing an install of Mint (an ubuntu derivative) Worked a charm to get my 8800GT installed. Never been easier.

 As a newbie to ubuntu and Linux, nothing is easy at the moment.

So I have downloaded a *.deb file. What do I do with it now??

---

### Post by mellowd on 2007-12-20
Go to the folder you installed it and type this:

```
sudo dpkg -i filename.deb
```

---

### Post by freymann on 2007-12-20
> **mellowd said:**
> Go to the folder you installed it and type this:

```
sudo dpkg -i filename.deb
```

Ok, envy did a lot of stuff that I certainly wouldn't have been able to do manually.

I've rebooted, I see the nVidia splash screen, I was able to flip on desktop effects.

When I go to Applications>System Tools>Nvidia Settings I get:

You do not appear to be using the NVIDIA X driver. Please edit your XCONF file.
Run nvidia-xconfig as root and restart.

(which I thought it did already)

So I did that, but now I'm being dragged out the door before I can reboot, so I will let you know how it went in a few hours.

Thanks very much. Envy seems like a great program!

---

### Post by mellowd on 2007-12-20
> **freymann said:**
> Ok, envy did a lot of stuff that I certainly wouldn't have been able to do manually.

I've rebooted, I see the nVidia splash screen, I was able to flip on desktop effects.

When I go to Applications>System Tools>Nvidia Settings I get:

You do not appear to be using the NVIDIA X driver. Please edit your XCONF file.
Run nvidia-xconfig as root and restart.

(which I thought it did already)

So I did that, but now I'm being dragged out the door before I can reboot, so I will let you know how it went in a few hours.

Thanks very much. Envy seems like a great program!

Great to hear! One of the best little apps I've come across!

---

### Post by freymann on 2007-12-21
> **mellowd said:**
> Great to hear! One of the best little apps I've come across!

 Envy reminds me of a little script I used to use that would download, compile and install apache, php, and mysql for you. For the life of me I can't remember what it was called!

 Envy is a great package indeed.

 I seem to have desktop effects enabled now. My screen looks a little sharper than it was (which is great!). 

 I still get this message:

When I go to Applications>System Tools>Nvidia Settings I get:

You do not appear to be using the NVIDIA X driver. Please edit your XCONF file.
Run nvidia-xconfig as root and restart.

I don't know what that means? I ran the root command, rebooted, same message. I looked in my xorg.conf file and it's definitely using the new drivers.

So now that I have this working, how do I get "the cube?"

Thanks for your tip too. I'm going to look at the link(s) in your sig too.

---

### Post by xtracool_protik on 2008-05-06
Thanx a lot guys that one helped a lot
 I'm complete dummy to Ubuntu couldn't get my 8400 running on DELL XPS but this thread done it for me
However envy does a lot of things but when it restarted my laptop it just shows a black strap in middle of screen thats all

---

