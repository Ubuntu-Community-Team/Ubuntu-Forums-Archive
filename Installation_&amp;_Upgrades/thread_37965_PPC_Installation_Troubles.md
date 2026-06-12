---
title: "PPC Installation Troubles"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by dblyth on 2005-05-29
Just burned the install cd last night and installed ubuntu on my imac last night, but unfortunately ran into a few problems last night.

During installation, I got an error during the Multi-something or other step...can't remember exactly, and I forgot to write it down. 

Anyway, after it installed, and came to the login screen, I typed in my username and password. As the login process continued (with the icons and all that) I got a few error messages pop up.

One of them was: 
Nautilus can't be used now, due to an unexpected error. 
Showing more info: Nautilus can't be used now, due to an unexpected error from bonobo when attempting to register the file manager view server.

Another 7 were: 
The panel encountered a problem while loading:
OAFIID:GNOME_ShowDesktopApplet, _NotificationAreaApplet, _Panel_Trash_Applet, _MixerApplet, _ClockApplet, _WorkspaceSwitcherApplet, _WindowListApplet

And finally, the last one was: 
There was an error starting the GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly. The settings Daemon restarted too many times. GNOME will still try to restart the settings Daemon the next time you log in.

This happens both in the regular GNOME login session, as well as the GNOME failsafe login.

---

### Post by shmendrick on 2005-10-10
I had similar problems.  see this [http://www.ubuntuforums.org/showthread.php?p=399223#post399223](http://www.ubuntuforums.org/showthread.php?p=399223#post399223)
post. 

there is a link off that thread that helped me discover the problem.

---

### Post by amanda on 2005-10-14
The suggested solution is to fix the system time or the hardware clock, which I can't find good instructions on. 

The time and date settings interface wants a root password, which I don't have. I had to open a terminal shell, say "sudo -s" and then change the root password. I still got an error indicating that "the configuration could not be loaded/there was an error running the backend script"

I was finally able to set the date with the "hwclock" command, but I still get a bunch of errors:
* The panel encountered a problem while loading OAFIID:GnOME_ClockApplet ... unknown corba exception id 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'
* same error for GNOME_BattstatApplet
* same for GNOME_Panel_WirelessApplet
* GNOME_NotificationAreaApplet

I still can't start the GNOME settings daemon, it "restarted too many times" and I am getting the same Nautilus /Bonobo error.

FINALLY:
this what i did, it took me way too long to figure out:
 sudo hwclock --set --date=10/12/2005
 sudo hwclock --hctosys

Now Gnome launches without errors, but I approved some of the appplet deletions the first few times I tried to start. I still can't just use the System Settings Gui to set the date and time. Do I need to restore those applets? How?

---

### Post by amanda on 2005-10-19
An update: 

I fixed the hardware clock and reinstalled from scratch. This time I did a few things differently: 
* I used a known good network connection (I haven't tested the old one, so I don't know whether or not it was part of the problem, but I definitely wasn't able to connect to the network during my first install.)
* I used 5.10 -- the original version was 4.x something that I made a friend mail to me after earlier attempts to download and burn a boot CD came to naught. I made a new boot cd and this one worked.
* I charged the battery -- during the original install the powerbook had been basically drained completely of power and sitting unplugged on a shelf for four months.

So this time, with a full battery, an accurate hardware clock, a good network connection and breezy badger 5.10, I was able to do a seamless install.  I have no idea which of those pieces was the key, but I did get everything in order.

---

