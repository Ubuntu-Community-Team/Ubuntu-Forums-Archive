---
title: "Edgy upgrade froze; xorg broke"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by darklemming54 on 2006-11-05
to upgrade edgy i used gksu "update-manager -c".  after the files were downloaded and installing, the update manager froze.  I had a half upgraded edgy install.  When i restarted (bad idea) with my old kernal, Xorg was broken.  I ran "sudo dpkg-reconfigure -phigh xserver-xorg" but it said that it couldn't do anything becuase Xorg is broken.  I have a back up to my files, but i don't want to do a fresh install.

---

### Post by .t. on 2006-11-05
In a terminal, do "sudo aptitude install ubuntu-desktop" (if you're using Ubuntu, if not, replace ubuntu-desktop for "kubuntu-desktop" [Kubuntu] or "xubuntu-desktop" [Xubuntu]). That should reinstall Xorg.

---

### Post by darklemming54 on 2006-11-05
this worked, thanks

---

### Post by FastZ on 2006-11-07
Well, here's my story.  I thought I'd try to install Beryl on Edgy and screwed up the install so I tried to remove all the stuff I had installed for Beryl and then everything went downhill.  Now when I reboot the machine and boot into Ubuntu, ill get a blue screen error that says:

```
Failed to start X server (your graphical interface).  It is likely that it is not set up correctly.
Would you like to view the X server output to diagnose the problem? 
Yes     No
```I select Yes and this is what it gives me:

```
X Window System Version 7.1.1
Release date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operation System: Linux 2.6.15.7 i686
Current Operating System: Linux swint 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org to make sure that you have the latest version
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice,
(II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 7 17:57:04 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
         <ok>
```Now...  when I was uninstalling the packages I had installed when I was trying to install Beryl, I had installed some nVidia drivers and then uninstalled them.

So now I am stuck in the terminal and dont know what to do.  How can I install the nVidia drivers from the terminal when I can use a text editor to edit my sources.list file to include the repositories for the drivers?

Found it.  Apparently I had already added the correct repositories for getting the nvidia drivers so I just did the following:

```
sudo apt-get install nvidia-glx
```and then:

```
sudo apt-get upgrade
```then did the following:

```
sudo nvidia-xconfig
```to backup and update my xorg.conf file.

then a:

```
sudo reboot
```to restart the computer to see if everything worked...which it did.  Thank God!

Before doing the above steps, I had tried to reinstall the Ubuntu-desktop, which did not help me in my situation.  It did in yours obviously.  Anyway, I thought I would post this fix on here since it is sorta related in a way, just in case someone is looking for another option on how to fix a broken xorg server problem.

---

