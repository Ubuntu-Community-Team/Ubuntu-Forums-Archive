---
title: "Maverick... unity suddenly installed o_O"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by Holker on 2011-08-18
Last night I checked for updates and installed Playonlinux 4.0.2 from 4.0.1 and shut down my laptop after that.

This morning I started up my laptop with dualboot; in Grub I selected to start up with Maverick OS and it started loading it up; Ubuntu 10.10 loading screen was normal; Login screen normal too; typed in password and pressed enter and then I get the following error message:
> Could not update ICEauthority file /home/holker/.ICEauthority
[Close]I closed the error message and then I get the following error message:
> There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)
[Close]Closed that error message as well and then suddenly I have a Unity desktop, which I never installed or asked for! o_O And of course another error message appears:
> **Nautilus could not create the following required folders: /home/holker/Desktop, /home/holker/.nautilus**
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.
[Close]I closed this, tried to start up Firefox, but it wont... I can open terminal and also text editor... I checked my directory /home/holker/ and there are just 2 files in there;
Access-Your-Private-Data.desktop containing the following text:
```
[Desktop Entry]
_Name=Access Your Private Data
_GenericName=Access Your Private Data
Exec=/usr/bin/ecryptfs-mount-private
Terminal=true
Type=Application
Categories=System;Security;
X-Ubuntu-Gettext-Domain=ecryptfs-utils

```and a README.txt file containing text:
> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
What the hell is going on??? Have I been hacked? :confused:  And how do I get things back to the normal configuration of last night WITH all my saved website-work in my /home/holker folder?
Help please?

---

### Post by Holker on 2011-08-19
All right, I have been looking in this forum for possible solutions and I found this thread: [http://ubuntuforums.org/showthread.php?t=1366173&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1366173&highlight=ICEauthority)
I tried the following things: ```
sudo chown -R holker:holker .ICEauthority
```Didn't recognise the -R, so:```
sudo chown holker:holker .ICEauthority
```didnt work, so I was worried there was a capitol error and tried:
```
sudo chown Holker:holker .ICEauthority
``` and ```
sudo chown holker:Holker .ICEauthority
```Command not found, was the result. Then I tried the next advise in the thread: ```
sudo apt-get remove nautilus
sudo shutdown -r now
sudo apt-get install nautilus
sudo shutdown -r now
```it reinstalled nautilus, but nothing changed... so up to the next tip in the thread:
```
ls -la /home/
sudo chown holker:holker /home/holker
```nothing... next thing:```
sudo apt-get install gnome-panel
```Latest version already installed... so I then tried the command in the README.txt file... ```
sudo ecryptfs-mount-private
```...which didnt work either.
As you can see I have been busy, but all I got now is an extra error in the Ubuntu 10.10 loading screen before the login screen, so all in all I think I just made matters worse... #-o

Can someone please help me?

---

