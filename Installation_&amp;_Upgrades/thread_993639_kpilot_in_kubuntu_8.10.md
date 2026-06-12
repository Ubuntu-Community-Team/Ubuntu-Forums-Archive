---
title: "kpilot in kubuntu 8.10"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by canoe529 on 2008-11-25
Hi folks,
I just upgraded to 8.10. Unfortunately, I lost the ability to sync with my centro because kpilot wasn't installed. When I dink around with synaptic and add the "unsupported" repository to try to install it, I get the following messages:

To be installed: libkcal2b libkdepim1a libkmime2 libktnef1
kpilot:
 Depends: libbluetooth2 (>=3.14) but it is not installable

So kpilot won't install because I've got libbluetooth3 instead of libbluetooth2 installed, and the dependencies aren't recognizing that. 

Is there a way I can force the installation of kpilot? I don't even use the bluetooth functionality. It is really important that I get this working again, otherwise I may have to drop back to Hardy, which sounds like a whole new reinstall all over again. 

Would it be possible to sideways-convert to Ubuntu, then install kpilot? I prefer KDE as my WM, but will take Gnome if it allows me to run kpilot successfully.

Thanks

---

### Post by iheartubuntu on 2008-12-06
Im having the same problems as you are. I successfully installed Kpilot on another computer using:

sudo apt-get install kpilot

But that doesnt work on this computer Im using right now. I have no idea what the differences are. Both are (were) fresh installs of Ubuntu 8.10. I did have KDE-Desktop installed on my other system, but I have it now installed on this system as well. Still no luck with Kpilot.

And let me just say Kpilot is GREAT. Much nicer and simpler than the Palm software for Windows, and bay far better than Jpilot which I could never quite get working right (plus crappy GUI).

---

### Post by jglen490 on 2008-12-22
You might be able to add the Hardy repos and then try to get libbluetooth2 from there.  Having the two libraries should not be a problem.

---

### Post by roystreet on 2009-01-23
Hi, I'm having all sorts of troubles with using J-Pilot.  Plus, I'd rather not use the GUI it has - Not so nice looking.  Anyway, how do I get kpilot on my machine.  I use kubuntu 8.10 also.  I can't figure out how to download it in the first place, nor install it. 

I'm new at this, but I really want to learn it & eventually totally convert over to linux.  So hand holding is needed at times.:)

I use a Palm TX & USB connection.  I noticed the words used in this thread make me think it has something to do with blue tooth?  Not sure, but I'm looking for USB.

Thanks A Bunch,
  ~roystreet

---

### Post by epimeth on 2009-03-16
I can't get kpilot working properly either...
The palm is a T|X from a while back so it is not updated... the palm OS  version is Garnet 5.4.9, so getting configuration for exactly that would be a big help.

I get the following error when running from command line:
KPilot configuration version  520  newer than stored version

the gui, meanwhile loads into configuration mode.

I lost my usb cable and so I want to use bluetooth.  I was able to (somehow) configure my way into adding my laptop onto the T|X's trusted connections and also have the laptop see the palm as a device (if not actually connect to it).

so now I am at a point where I need to enter configuration data for a device that doesn't exist (/dev/pilot) of course I don't have that device, so I just hit OK figuring that I can get back to configuring a device later.  so now I get:
The configuration file for KPilot is out-of date. Please run KPilot to update it.
DETAILS:
The configuration file is outdated. The configuration file has version 0, while KPilot needs version 520. Please run KPilot and check the configuration carefully to update the file.
Important changes to watch for are: Renamed conduits, Kroupware and file installer have been made conduits as well. Conflict resolution is now a global setting. Changed format of no-backup databases. Calendar, ToDo, and Contacts conduits are now using KDE4's Akonadi server and require valid Akonadi resources to sync. 



so... bottom line I figure I need a help with two things:
1) get the laptop and the palm to connect over bluetooth
2) configure kpilot to sync with the palm.

any takers? :-)

---

### Post by knitmom on 2009-06-02
I'm having the same issues too!  Especially configuring akonadi.

I'm running dual boot, Kbuntu (32 bit version) and Windows vista 64 - which doesn't work with my Palm T|X.  The only work around to get it to work with vista 64 is the bluetooth connection and that is the only time I've seen that mentioned.

Now, with Kpilot, I've had luck getting it to read and backup my palm pilot when I set "Pilot device" to usb:  under the configuration menu.  So maybe if you can find the right command for the bluetooth, it might work.

I would love to use Kontact because of the way it looks and all it has to offer.  I was using JPilot and it worked great until something broke, it won't load, not sure why it stopped working.  It was a lot easier to set up.  Maybe try that to see if the bluetooth connection works, you could also see what they use for the bluetooth setting.

Now, in the Akonadi I'm using the default file locations for the calendar and the address  book for Kontact.  But I get an error message saying unkown error, the collections can't be created.  I really want this to work.  I would prefer to use Kbuntu all the time and actually be able to sync my palm.  Evolution doesn't work correctly when I sync, so that is out.

Thanks,

Knitmom

---

### Post by helmut_hed on 2009-09-28
Maybe you could give these directions a try:

[http://ubuntuforums.org/showthread.php?t=1239558](http://ubuntuforums.org/showthread.php?t=1239558)

I am exploring this too.  Good luck.

---

