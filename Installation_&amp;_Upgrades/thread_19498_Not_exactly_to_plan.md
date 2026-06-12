---
title: "Not exactly to plan"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by Telderoth on 2005-03-12
I can't wake the mouse pointer up and connecting to the net is becoming problematic. I did have errors during installation and I'm wondering whether a fresh install might fix the problems - these are the only two I seem to have. I have a dual boot system and linux resides on a separate disk. Does anyone know if you can resintall Ubuntu V4.10 over itself similar to Windows and missing files will either be installed or existing files repaired?  :evil:

---

### Post by alastair on 2005-03-12
Before taking the drastic step of reinstalling, lets try to find out the problems. One at a time.

1) You had "errors" during install? What about now?

Check the system logs e.g.

/var/log/syslog

Anything in there (from boot up) that looks wrong?

2) Mouse pointer?

X is a problem somewhere. X has logs in :

/var/log/X*.log

Anything look bad in there?

Note - if X goes wrong, you can always restart it (kill it and back to login screen) using CTRL+ALT+BACKSPACE.

---

### Post by az on 2005-03-12
Did your mouse ever work?  How old is your computer.  I had to load the (blacklisted because it is depreciated usbmouse modules to make a certain mouse work for me on an old computer...)

What is wrong with the internet.  Are you on dialup, cable, dsl?

If you have a decent connection, 
sudo apt-get update
sudo apt-get dist-upgrade

Will bring in some new packages.  Maybe there are some bugfixes.  You need to be more specific, though.

---

### Post by alastair on 2005-03-12
> I have reconfigured XFConfig-4, but I don't have imwheel (the mouse is logitech 4 button mouse). That's why I think some file must be corrupted somewhere because on one else seems to have the same problem. I've also had trouble getting my external Swann 56K modem to work so I gave up for now and downloaded imwheel, transferred it to floppy, mounted it but when I went to extract it via 'dpkg -i/media/floppy/*.deb' it said it couldn't find the file. This is why I'm frustrated. I'd be really happy if I could get the mouse to work, everything else does! Can you assist? Once I reboot, which I have to do, I'll check the logs as you suggest. The only reason I thought of reinstalling was maybe it would be easier?

OK - private message - best in the forum.

I don't know the right mouse setup - I have a straightforward PS/2 style wheel mouse, and always have had. A search on google for :

logitech 4 button mouse linux

Turned up quite a bit of information though. What exact mouse model? PS/2? USB?

You could also try reconfiguring X via :

dpkg-reconfigure

You have XFree86 installed - you need to find out the base XFree package and pass that as an argument. I have Xorg - so I would use :

dpkg-reconfigure xserver-xorg

Check what you have installed (perhaps : dpkg -l '*xserver*').

---

### Post by Telderoth on 2005-03-13
[QUOTE=alastair]OK - private message - best in the forum.

I don't know the right mouse setup - I have a straightforward PS/2 style wheel mouse, and always have had. A search on google for :

logitech 4 button mouse linux

Turned up quite a bit of information though. What exact mouse model? PS/2? USB?

You could also try reconfiguring X via :

dpkg-reconfigure

You have XFree86 installed - you need to find out the base XFree package and pass that as an argument. I have Xorg - so I would use :

dpkg-reconfigure xserver-xorg

Check what you have installed (perhaps : dpkg -l '*xserver*').[/QUOTE]

I looked at Google and it suddenly dawns on me. All this palava trying to reconfigure my mouse so I can use extra buttons when that's not the problem. I'm happy for Ubuntu to look at the mouse as a PS2 the same as windows. I've reconfigured X twice, once for Explorer and once for Mouseman. It makes no difference, the arrow just will not move!!!

One thing that does work is that instead of the hourglass, linux has that circle and it does it's thing on boot up but here's the thing, I disconnected the mouse and rebooted, the arrow was still there? Why does this happen? That's why I was thinking of resintalling, thinking that something was corrupted. If we can look at it this way - this is a straight forward USB PS2 which will not move. 

What about Hotplug? Is this not similar to Add/Detect hardware in Windows? I did have a modprobe error in relation to hotplug when I first installed so I downloaded the starter guide and found the fix. It loads now - does this have anything to do with it? It's like linux won't detect the mouse similar to the modem. Why does linux have problems with detecting peripherals? I really want to get this fixed and so far it looks as if I'm the only one with the specific problem?

---

### Post by alastair on 2005-03-13
Post your X config and last log file :

/etc/X11/XF86Config  (or perhaps /etc/X11/xorg.conf)

/var/log/X*.0.log  (whichever log file name it is)

---

