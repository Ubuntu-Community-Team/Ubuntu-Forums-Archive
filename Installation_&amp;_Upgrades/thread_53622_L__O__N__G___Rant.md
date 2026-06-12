---
title: "L  O  N  G   Rant"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by Tomlin on 2005-08-01
I'm sorry, but I have to rant here!!!

I'm trying REALLY REALLY hard to like this distro, but....

1 ) No way to install from floppies (for machines that can't boot from CD ROM). However, I found a solution called smbinst.exe that allowed me to boot from the CD.

2 ) smbinst.exe gave me a "Disk error! 0xAA". More searching the forum...nothing worked.

3 ) Swapped CD ROM drives and got smbinst.exe to begin the install.

4 ) Thirty minutes later, CD ejected and 2nd part of install began with a re-boot....and ended with a "GRUB Geom Error".

5 ) More searching the forums AND the 'net. Nothing found that worked.

6 ) I tried one last time to install (after 4 unsuccessful attempts) and noticed a "framebuffer error" of some sort which flashed by too fast to read anything more than that. I tried again using the "linux debian-installer/framebuffer=false" option which worked.

7 ) 2-3 hours later (I gave up watching and had breakfast) I return to find a login screen.

8 ) Frustrated by lack of "true" root login. Extra steps needed to make ANY change to the OS settings.

9 ) When logging in or using the search function on these forums (using Firefox in Ubuntu) I keep getting a popup window stating:

The information you have entered is to be sent over an unencrypted connection and could be easily read by a third party.

Are you sure you want to continue sending this information?

[ ] Alert me whenever I submit information that's not encrypted.

EVERY TIME......Is there NO WAY to change this? It doesn't happen on ANY other machine with ANY other browser (INCLUDING Firefox on windoze 2000, 98, RH 8 and Suse 9). What gives?????

10 ) I can't change the screen resolution. I followed the advice of others on the forum, ie adding the refresh and sync rates for my monitor (which I got from the X config file on my RH 8 and Suse9 machines.....both of which detected it AUTOMATICALLY). The monitor and graphics card are capable of up to 1024x768. It's at 800x600 now.

11 ) Starting a terminal window (as myself) using:

gedit /etc/X11/xorg.conf

brings the file up in gedit, but doesn't allow me to change anything.

HOWEVER....

Starting a root terminal window (and supplying a password) using:

gedit /etc/X11/xorg.conf

gives me this error:

(gedit:5342): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified 

BUT THEN opens the file and allows me to edit and save it?

I hate to sound like a whiner, but I started this fiasco on Saturday morning. It's now Monday afternoon and I still haven't found a way to change screen resolution. This is ridiculous.

Okay, I'm finished ranting. I'll go and have some lunch.

---

### Post by BKonkle on 2005-08-01
I can't say much about your other installation woes, because my installation was a pretty smooth "it just works" installation.  I've installed Hoary several times now (I like to tinker with things), and I notice that when I walk away and leave the installation unattended, when the debconf window for xserver-xorg pops up, it will timeout with the default settings and not allow me to change the resolution later.  It sounds just like the problem you are having.

Long story short, to go back and reconfigure your xserver, type the following:

```
sudo dpkg-reconfigure xserver-xorg
``` 

It will give you a lot of options about keyboard and mouse. . . just hit enter through most of it.  The default options are *usually*  fine.  When you get to the spot where it asks you about resolutions, just make sure you enable the resolution you want to use.

I hope this helps!

---

### Post by az on 2005-08-01
Smart boot manager is on your cd.  It is in the install folder.

You can log in as root, if you want to.  Just create the root account.  There is not one by default.  There is plenty of documentation about that.

It is not recomended to log in as root in an X session, though.


And if you really really want to avoid the command line, you can use synaptic to reconfigure your xserver-xorg package.  Just pick the package and hit configure in the package drop-down menu.  When you get to the monitor section, pick medium and find the resolution and frequency you want.


It will probably not correctly autodetect your video hardware from within an X session, but using the defaults provided by debconf, you should be ok.

---

### Post by az on 2005-08-01
Oh, and file a bug report about the framebuffer thing.  Check to see if it is already filed, of course.

bugzilla.ubuntu.com

---

### Post by jasmuz on 2005-08-01
About your Sudo issues, you should of read:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Tomlin on 2005-08-04
Thanks for the replies guys.

BKonkle - I succeeded in changing my resolution to 1024x768. After the 1st try, I received an error and it booted up in text mode. I'm not sure what I did/didn't do, but I re re-configured and it worked...thanks.

azz - I received the distro with "LINUX Format" magazine. I guess there are some things (like smb) missing. I searched the 'net to find that.

jasmuz - I did read the 'wiki' blurb about root/sudo. I guess I fail to see the difference (other than a timeout after 15 minutes). If you log in as root, like I do in Suse, the privilege lasts the entire session & you don't have to enter a password for every change you make. Its not a big deal, I guess. I'm just used to logging in as root (at boot time), making any changes to the system I need, and then logging in as a normal user. Then again, I got lazy and started doing things in GUI mode.

Thanks again for your time. I just got cranky after a 2 day ordeal :grin:

---

