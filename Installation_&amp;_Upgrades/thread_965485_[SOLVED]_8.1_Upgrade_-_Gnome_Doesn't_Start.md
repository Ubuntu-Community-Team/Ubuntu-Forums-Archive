---
title: "[SOLVED] 8.1 Upgrade - Gnome Doesn't Start"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by N00bB00b on 2008-10-31
[COLOR="Red"][EDIT] I am nearly done, I believe.  See the rest of this thread for more.  If it works for you, please drop a thank you.  When I've got the whole thing done I'll put all of it up here.

NOTE:  If when you did the 8.04 to 8.1 upgrade you told the installer to remove unused packages, you are in the same boat as the rest of us.  As I have found out while working on this thread, that is a problem that is fixed by reinstalling them.  HOWEVER, there are many reports from folks that just downloaded the 8.1 live CD and used that to do a clean install that had good results.  That is probably the faster route.  Don't forget to either backup your /home directory or put it on a separate partition first.  If you want to do the partition route, go to Add/Remove Programs under the Applications menu and pick Partition Editor.  If you have a black screen, check note 3 below for how I got Gnome back up and then started to recover from my mistake. [/COLOR]

TAGS for this post so that others who are struggling with this topic can find at least some relief: (Gnome, graphic login window, gui - any others I should add?)
[/EDIT]

I just upgraded from 8.04 (all patches) to 8.10.

Reboot - window manager doesn't start.

I then tried to apt-get upgrade and apt-get update.  This does not fix the problem.

startx results in

Current operating system Linux junk 2.6.24-21-386 ...
Build Date 13 June 2008 ...

Errors to screen:
(EE) Failed to load module "vesa" (module does not exist, 0)
(EE) Failed to load module "synaptics" (module does not exist, 0)
(EE) Failed to load module "mouse" (modle does not exist, 0)

Fatal scren error:
no screen found
giving up.

xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

---

### Post by N00bB00b on 2008-11-03
[COLOR="Red"]What I tried in this post doesn't help at all:[/COLOR]

I have now tried the following:

```

$ sudo /etc/init.d/gdm stop
$ sudo dpkg-reconfigure xserver-xorg
$ sudo /etc/init.d/gdm start

```

still no joy.

---

### Post by N00bB00b on 2008-11-03
[COLOR="Red"]In this post we finally get somewhere - however there is still work to do.  NOTE:  After executing the apt-get commands, you have to reboot to get use of your keyboard back.  Keep reading because there is still more to do.[/COLOR]
Now I've tried

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Boy does that take forever.  I could have done the install from the LiveCD faster (and the download didn't take hours and hours and hours).

Now I get Gnome and a graphical login, but no keyboard.  Mouse works.

Reboot again.  Keyboard works, BUT
1) I have an error that the Configuration Defaults for the Gnome Power Manager have not been installed correctly.
2) Applications I installed are gone.  They appear on the Applications menu, but they're not there.  This makes sense if there are additions stored in my home folder for applications I add.
3) Firefox and OpenOffice.org aren't in the Applications menu, and they aren't on the screen.  Now it's time to reinstall those.
4) Startup program list remains from before.



NOTE:  None of this is unexpected.  After reading a boatload of posts, people who have done the upgrade and chosen to remove old packages have run into this issue after fixing this problem.

---

### Post by N00bB00b on 2008-11-03
Running the Update Manager resulted in another error, so I had to

```

sudo dpkg --configure -a

```

That fixed the Update Manager problem.

---

### Post by N00bB00b on 2008-11-03
Like other folks, I still don't have video, sound, or telnet yet, although I was able to run a Hardware Testing report that was (allegedly) successfully sent to Launchpad, and FTP worked.

nslookup check
ping     check
ifconfig check
ntp      nope -- ntp is the network time protocol.  Go into System->Administration->Time & Date.  Then hit the "Unlock" button, and in the Configuration popup choose "Keep Synchronized With Internet Servers".  Interestingly, selecting that option returns a message that NTP isn't installed, and asks you if you want to install it.  I confirmed, but NTP still didn't work.  UPDATE - rebooting fixed NTP.

Also, II recognized my wireless card.  That was a problem in HH.  We'll see if I can actually configure it.

In he Appearance Preferences, the Visual Effects are disabled.  Help doesn't seem to work, either.

---

### Post by N00bB00b on 2008-11-04
It should be noted that multiple people recommended just doing a reinstall from the CD after getting Gnome back up.  I might still do that, but I'm going to be stubborn about this for now while I download the full Live CD.

OK, now we have the "base applications" installed.  What a pain.  However, we don't have any options.  For example - I am still missing the following:

[LIST]
[*]System spellchecking
[*]OpenOffice spellchecking (that's right - if you use the Synaptic Package Manager from the Administration menu or Add/Remove... option from the Applications menu, you don't get spellchecking).
[*]Screensaver - an easy way to check for this is to go to the Power menu and pick "Lock Screen".  If it doesn't lock, you are missing it.
[/LIST]

Both of these appear to be available in some form from the Synaptic Package Manager - along with a host of other spellchecking items...

[LIST]
[*]Sound drivers
[*]Gnome Visual Effects (check the "Visual effects" tab in the Preferences->Appearance menu
[*]Open Office Help (go into OO.o and hit F1)
[*]Ubuntu/Gnome Help
[*]Flash Player
[/LIST]

I'm sure there's more but that's what I've found so far.

---

### Post by N00bB00b on 2008-11-04
[LIST]
[*]OpenOffice.org help can be found in the Synaptic Package Manager (System->Administration->Synaptic Package Manager).  Click on "Search" then "openoffice.org-help-en-us"
[*]OpenOffice Thesaurus is at openoffice.org-thesaurus-en-us
[*]Flash Player is at flash-nonfree
[*]OpenOffice.org spellchecker is in hunspell and hunspell-en-us.  [COLOR="Blue"]NOTE:  Even though OO.o THINKS that it has the spellchecking capability installed and running it doesn't. If you check Synaptic you will see that Hunspell isn't installed.[/COLOR] [COLOR="DarkOrchid"]Also note that installing hunspell and the correct dictionary fixes Tomboy notes and a variety of other applications spelling functions as well.[/COLOR]
[*]Ubuntu help is ubuntu-docs
[*]Screensaver is under gnome-screensaver
[*]Desktop Effects are under Compiz.  While installing Compiz enabled the page on the Appearance panel, it gave me an error.  I then also went to the Applications Menu, picked Add/Remove... and added Compiz (which I wouldn't expect to work because on that side it's supposed to be for KDE and not Gnome).  No change.  Rebootting...Now I get "Looking for Drivers" followed by "Desktop Effects Could Not Be Enabled".  So we're getting closer.  In Synaptic do a search for "glx" and "xgl" to help figure out what you need to install.
[*]Network Manager - yep.  I can't change IP addresses, which is a real bummer when I'm at home vs. work and I need to get on the net to work on this project.  After changing /etc/resolv.conf and using ifconfig I'm back at it.  HOWEVER, installing the Network Manager doesn't help me yet because I can't use it to switch setting families.  I still have to do it manually.
[*]Wow.  Even GRUB didn't get installed.  I really screwed this up by letting the installer delete the old packages.  Thankfully even that can be rectified.
[/LIST]

---

### Post by N00bB00b on 2008-11-04
Uh, OK, I have no idea how this happened, but after doing all of that, then making a Live CD so I could see what else was broken, my sound decided to start working.  Yes, I've rebooted a billion times so far.  Yes, I shut down (completely) first.

I built the 8.1 live cd, booted.  Sound works.  I ejected the CD and shut down.  Rebooted.  Sound works.  By the way, the easiest way to check your sound is to go to System->Preferences->Sound and test one of the effects.

Other things are still missing, e.g. the visual effects.

---

### Post by N00bB00b on 2008-11-12
That's it.  I finally gave up and clean-installed.  Everything works, and stuff that didn't work in 8.04 is now working as well.  Also, I clean-installed 8.04 in a separate partition, and that fixed various OTHER issues that I had before, too.

---

