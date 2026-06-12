---
title: "gdm 2.27.90-0ubuntu1 loops on startup"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-08-26
Anyone else affected?

After mornings updates, gdm just loops over and over again.
xterm session works
TTY's fails to launch...
Checking the logs and uploading them soon....

Kernel version doesn't matter.
radeon driver in use.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

```

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-lna850/socket
SSH_AUTH_SOCK=/tmp/keyring-lna850/socket.ssh

(gnome-settings-daemon:3306): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3306): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 28 requests (27 known processed) with 0 events remaining.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 1138 requests (1131 known processed) with 0 events remaining.
Window manager error: Unable to open X display :0.0

```

Latest updates:
```
Tue, Aug 25 2009 19:23:37 +0300
[INSTALL, DEPENDENCIES] indicator-session
[REMOVE, DEPENDENCIES] readahead
[INSTALL] indicator-applet-session
[INSTALL] sreadahead
[INSTALL] telepathy-idle
[UPGRADE] cpp 4:4.4.0-3ubuntu1 -> 4:4.4.1-1ubuntu2
[UPGRADE] ffmpeg 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] g++ 4:4.4.0-3ubuntu1 -> 4:4.4.1-1ubuntu2
[UPGRADE] gcc 4:4.4.0-3ubuntu1 -> 4:4.4.1-1ubuntu2
[UPGRADE] gdm 2.27.4-0ubuntu11 -> 2.27.90-0ubuntu1
[UPGRADE] indicator-applet 0.2.0~bzr326-0ubuntu1 -> 0.2.0~bzr326-0ubuntu2
[UPGRADE] libavcodec52 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] libavfilter0 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] libavformat52 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] libavutil49 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] libpostproc51 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] libswscale0 4:0.5+svn20090706-1ubuntu2 -> 4:0.5+svn20090706-1ubuntu3
[UPGRADE] tomboy 0.15.5-0ubuntu2 -> 0.15.6-0ubuntu1
[UPGRADE] ubuntu-desktop 1.161 -> 1.162
[UPGRADE] ubuntu-minimal 1.161 -> 1.162
[UPGRADE] ubuntu-standard 1.161 -> 1.162

Tue, Aug 25 2009 21:03:15 +0300
[UPGRADE] libgudev-1.0-0 1:145-1 -> 1:146-1
[UPGRADE] libudev0 145-1 -> 146-1
[UPGRADE] udev 145-1 -> 146-1

Wed, Aug 26 2009 00:18:03 +0300
[UPGRADE] e2fslibs 1.41.8-1ubuntu2 -> 1.41.9-1ubuntu1
[UPGRADE] e2fsprogs 1.41.8-1ubuntu2 -> 1.41.9-1ubuntu1
[UPGRADE] foomatic-db 20090819-0ubuntu4 -> 20090825-0ubuntu1
[UPGRADE] libcomerr2 1.41.8-1ubuntu2 -> 1.41.9-1ubuntu1
[UPGRADE] libss2 1.41.8-1ubuntu2 -> 1.41.9-1ubuntu1
[UPGRADE] openprinting-ppds 20090819-0ubuntu4 -> 20090825-0ubuntu1

Wed, Aug 26 2009 02:03:07 +0300
[INSTALL, DEPENDENCIES] libdrm-radeon1
[UPGRADE] apport 1.7-0ubuntu3 -> 1.7-0ubuntu4
[UPGRADE] apport-gtk 1.7-0ubuntu3 -> 1.7-0ubuntu4
[UPGRADE] libgl1-mesa-dri 7.5-1ubuntu1 -> 7.6.0~git20090817.7c422387-0ubuntu2
[UPGRADE] libgl1-mesa-glx 7.5-1ubuntu1 -> 7.6.0~git20090817.7c422387-0ubuntu2
[UPGRADE] libglib2.0-0 2.21.4-0ubuntu1 -> 2.21.5-0ubuntu1
[UPGRADE] libglib2.0-data 2.21.4-0ubuntu1 -> 2.21.5-0ubuntu1
[UPGRADE] libglu1-mesa 7.5-1ubuntu1 -> 7.6.0~git20090817.7c422387-0ubuntu2
[UPGRADE] mesa-utils 7.5-1ubuntu1 -> 7.6.0~git20090817.7c422387-0ubuntu2
[UPGRADE] python-apport 1.7-0ubuntu3 -> 1.7-0ubuntu4
[UPGRADE] python-problem-report 1.7-0ubuntu3 -> 1.7-0ubuntu4
```

---

### Post by Kazade on 2009-08-26
I haven't run my updates for a couple of days.. but last week I tried to add the xorg-edgers PPA (I'm also on an ATI card), and I got this behaviour. It would start logging me in, then I'd get dropped back at the GDM. The xorg-edgers PPA also installed this: libdrm-radeon1

I had to downgrade and remove it to get everything back running again. I'm guessing it's do do with that. (I'm on an HD3200 FWIW).

---

### Post by taavikko on 2009-08-26
Reported: [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/419126](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/419126)

---

### Post by pulpo69 on 2009-08-26
here the same problem: gdm loops on startup

---

### Post by taavikko on 2009-08-26
> **pulpo69 said:**
> here the same problem: gdm loops on startup

Are you running ATI GPU?

---

### Post by plun on 2009-08-26
> **taavikko said:**
> Are you running ATI GPU?

I am running ATI on my laptop and I can login.

but...there is a complete mess with crashed apps and .xsession-errors is flooded with crap..

Probably severe race condition errors....

---

### Post by taavikko on 2009-08-26
> **plun said:**
> I am running ATI on my laptop and I can login.

but...there is a complete mess with crashed apps and .xsession-errors is flooded with crap..

Probably severe race condition errors....

Most likely caused by the upgraded libdrm/mesa and not the gdm in itself.
I'm running HD3450 (rv 620)

xterm session works, though.

---

### Post by plun on 2009-08-26
> **taavikko said:**
> Most likely caused by the upgraded libdrm/mesa and not the gdm in itself.
I'm running HD3450 (rv 620)

xterm session works, though.

Well probaly several bugs.....

I filled my xsession-errors log and got 11000 events since reboot 1hour ago...so its a mess now...  

Alpha-testing...:)

---

### Post by pulpo69 on 2009-08-26
when will there be a fix for gdm-loop, it's really annoying if one
can't login.

---

### Post by taavikko on 2009-08-26
> **pulpo69 said:**
> when will there be a fix for gdm-loop, it's really annoying if one
can't login.

Bryce is on it. It'll be fixed in it's due time.

Start xterm session, you can use almost everything that way (wrecking my nerves also :) )
But I have an desktop unit which is running 9.10 KDE so no biggie.

---

### Post by Kazade on 2009-08-27
If there are people that still can't log in, you can create an xorg.conf and set the driver to Vesa... it'll be slow, but at least you'll be able to log in.

---

### Post by taavikko on 2009-08-27
> **Kazade said:**
> If there are people that still can't log in, you can create an xorg.conf and set the driver to Vesa... it'll be slow, but at least you'll be able to log in.

xterm session is way more fun than full desktop gnome-session :)
Too bad that the TTY's are b0rked, would use them instead of xterm.

---

### Post by pulpo69 on 2009-08-27
when the "loop" will be fixed?

---

### Post by taavikko on 2009-08-27
> **pulpo69 said:**
> when the "loop" will be fixed?

When they find the underlying defect and the cure for it, no sooner no later.

Use "vesa" for video-driver if in need of desktop.

---

### Post by ranch hand on 2009-08-27
I am using the generic driver for my 2400 ATI card as there is no other suport for it.

I cannot login to any other session as this is not a choice.  The only option is the acessiblilty stuff.

---

### Post by taavikko on 2009-08-27
> **ranch hand said:**
> I am using the generic driver for my 2400 ATI card as there is no other suport for it.

I cannot login to any other session as this is not a choice.  The only option is the acessiblilty stuff.

This issue seems to only affect r600 -> chipset owners.

You can use xterm session, then edit xorg.conf and add 
{Driver "vesa"} to Device section

To exit xterm session, issue "exit" command.

---

### Post by ranch hand on 2009-08-27
How do I get the xterm session from the recovery terminal?

Have used the "help" command before and do not remember "xterm" being an option there.  Could just be a case of dementia though.

---

### Post by taavikko on 2009-08-27
> **ranch hand said:**
> How do I get the xterm session from the recovery terminal?

Have used the "help" command before and do not remember "xterm" being an option there.  Could just be a case of dementia though.

You don't, thought you did an normal boot to gdm.
It's an option there.

If in recovery, enter root shell, after that same thing applies, edit xorg.conf and exit with "exit" command.

---

### Post by ranch hand on 2009-08-27
> **taavikko said:**
> You don't, thought you did an normal boot to gdm.
It's an option there.

If in recovery, enter root shell, after that same thing applies, edit xorg.conf and exit with "exit" command.
Yes I do try to use a normal boot.  There are NO options there at all.  Basically I am well and truely screwed when it comes to login.

I will try it from shell, at least I can get to it.

---

### Post by ranch hand on 2009-08-27
Well, hold on here.  Just opened the file from here (9.04).  What am I editting?
```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"false"
EndSection

```
Device?  To "vesa"?

---

### Post by taavikko on 2009-08-27
> **ranch hand said:**
> Yes I do try to use a normal boot.  There are NO options there at all.  Basically I am well and truely screwed when it comes to login.

I will try it from shell, at least I can get to it.

When booting up, default kernel
gdm opens -> click "user name" -> click session on bottom panel and choose xterm
finish login

When booting up recovery
Select root shell from the list that appears.

---

### Post by taavikko on 2009-08-27
```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
 Driver "vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"false"
EndSection

```
> Device?  To "vesa"?

The corrected version is above, under device section we just added the driver line.

---

### Post by ranch hand on 2009-08-27
OK, did that.

Will switch drives and give it a whack.

---

### Post by ranch hand on 2009-08-27
I am happy to report that I am in and posting from one of my 32bit installs (an update from 9.04).  I will do the same to the rest of the buggers.  Makes life easier.

Also, now I do have options at login.  This is nice.

Thanks a bunch.

---

### Post by taavikko on 2009-08-27
> **ranch hand said:**
> I will do the same to the rest of the buggers.  Makes life easier.

Thanks a bunch.

Why, all of them? then you have to revert the change when the fix arrives.

---

### Post by ranch hand on 2009-08-27
I am driven.

I have done it and am glad.  I guess just checking would have been enough but this was kind of interesting.

I have installed 2 of each alpha.  A clean install and an upgade.  None of the clean installs and one of the upgrades had No /etc/x11/xorg.conf file.

---

### Post by pulpo69 on 2009-08-28
is this bug fixed now? anyone tried it?

---

### Post by taavikko on 2009-08-28
> **pulpo69 said:**
> is this bug fixed now? anyone tried it?

subscribe to this
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126)

When it says that "fix released" we're clear.

---

### Post by taavikko on 2009-08-28
If you set DRI off in xorg.conf you can login to gnome once more.

---

### Post by ranch hand on 2009-08-29
I have just gotten my 32bit 9.10 OS' (clean installs) to upgrade to -8.

Can not boot to the buggers.

I have another 9.10 that is a 9.04 upgraded to 9.10 and it is working fine with -8 and the xorg.conf with the added "Driver  "vesa" ".

The 2 clean install, to get to the login screen, need to have the Driver line commented out.  This does get the screen up but, of coarse, it just loops.

I have no idea what this DRI bussiness is but tried it in place of the Driver line and I am back to text login, just as with the Driver line active.

I will say, though, that -8 does shut down very nicely with the command "sudo reboot".

I have 4 64bit 9.10 variations and they are all working fine with the Driver line active in -8.

---

### Post by taavikko on 2009-08-29
> **ranch hand said:**
> I have just gotten my 32bit 9.10 OS' (clean installs) to upgrade to -8.

Can not boot to the buggers.

I have another 9.10 that is a 9.04 upgraded to 9.10 and it is working fine with -8 and the xorg.conf with the added "Driver  "vesa" ".

The 2 clean install, to get to the login screen, need to have the Driver line commented out.  This does get the screen up but, of coarse, it just loops.

I have no idea what this DRI bussiness is but tried it in place of the Driver line and I am back to text login, just as with the Driver line active.

I will say, though, that -8 does shut down very nicely with the command "sudo reboot".

I have 4 64bit 9.10 variations and they are all working fine with the Driver line active in -8.

Too many words, head hurts... :)
Add below the driver line
{Option "DRI" "0"}
You can remove the Driver line.

My xorg.conf
```
tta@dv5:~$ cat /etc/X11/xorg.conf 
Section "Device"
        Identifier "Configured Video Device"
        Option	"DRI"	"0"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection

```

---

### Post by ranch hand on 2009-08-29
Ah, I really do need to learn the right way to add these things.

My line was just
```

DRI   "0"

```
No "Option"

What a moronic noob.

I will try it again in a bit.  Need to get to the auto parts place for truck parts.

---

### Post by taavikko on 2009-08-29
> **ranch hand said:**
> Ah, I really do need to learn the right way to add these things.

Simple advice, check the "man" pages, they're written so they could be studied.
In this particular case, it's "man xorg.conf"

---

### Post by ranch hand on 2009-08-29
> **taavikko said:**
> Simple advice, check the "man" pages, they're written so they could be studied.
In this particular case, it's "man xorg.conf"
I do actually go to man pages.

In this case I have a lot of studying to do as I understand each word fine but the whole makes no sense to me at all.  Just need to get a geek dictionary or a geek to agricultural translator.

I will be working on this.  Never fooled around in the xorg stuff.  No need to.  There appears to be a need now.

Thanks a bunch.

---

### Post by pulpo69 on 2009-08-29
my xorg.conf is empty (blank, no entries.

---

### Post by taavikko on 2009-08-29
> **pulpo69 said:**
> my xorg.conf is empty (blank, no entries.

Default install doesn't provide one, since autodetection and configuration.
If you're unable to login, use my xorg.conf to gain access to desktop.

---

### Post by pulpo69 on 2009-08-29
tanks a lot. it worked with your xorg.conf. i'm now back in my gnome desktop.

---

### Post by ranch hand on 2009-08-29
Well now I am pretty happy.  Booting to all of my 9.10 OS'.

I wonder why this is different in 32bit than 64bit though.  Seems a bit basic to have a real difference between the two.

---

### Post by Duskao on 2009-08-31
I'm having the same issue with it looping. I was hoping that it would fix it's self if I waited a bit and did "sudo apt-get update" then "sudo apt-get upgrade". Still with the loop though. So I gather it's a xorg thing? I was trying to follow along with the prior posts but it's almost 2AM right now and I just got home from work, so I will read the rest later. Can I get a summation by chance?

---

### Post by trebach on 2009-09-05
Try the instructions at [https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon)

---

### Post by taavikko on 2009-09-05
> **trebach said:**
> Try the instructions at [https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon)

That actually is only temporary, the libgl1-mesa-dri doesn't provide the r600_dri.so file,
Which is equivalent to running xorg.xonf with DRI off.

So one can get the functionality back by adding
Option "DRI" "0"
to xorg.conf on normal Karmic packages. No need to resort to ppa's.

Doesn't anyone read the posts already made?

---

### Post by tsger on 2009-09-05
Read how I resolved the ATI issue [**HERE**]("http://ubuntuforums.org/showpost.php?p=7902691&postcount=11")

---

