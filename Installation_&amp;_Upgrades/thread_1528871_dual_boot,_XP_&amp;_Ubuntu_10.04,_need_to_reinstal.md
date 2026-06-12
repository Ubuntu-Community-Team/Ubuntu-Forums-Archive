---
title: "dual boot, XP &amp; Ubuntu 10.04, need to reinstall ATI driver from command line, novice"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by MatadorMac on 2010-07-11
In trying to get my SKYPE audio working with my webcam I had been working with ALSA after deinstalling the Ubuntu sound applet as directed/required?
 
After getting frustrated with ALSA and not fixing my Skype issues I wanted to return to the normal sound config. I deinstalled ALSA, everything ALSA. This seems to have taken out my ATI video card driver.
 
I can't get past the screen "Ubuntu will now use low resolution graphics, temporarily". After selecting "yes" it goes into endless screen repeats. When I click "cancel" the tty command line then comes up and I can log in.
 
But then I am stuck. I don't how to go further. I think I should or could reinstall my ATI video card driver by the command line and then configure it.
 
Any advice to get on the road to recovery is greatly appreciated.
 
Thank you
 
Mark MacKenzie

---

### Post by tmack2 on 2010-07-11
Try this to correct your issue
Choose, "system". Administration, Hardware drivers. look for your driver. uninstall then re-install from there.

---

### Post by oldfred on 2010-07-11
I have nvidia, but saved this link. Not sure if it is current or not.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by MatadorMac on 2010-07-12
> **tmack2 said:**
> Try this to correct your issue
Choose, "system". Administration, Hardware drivers. look for your driver. uninstall then re-install from there.
 
Thanks, I would if I could but I can't get into the graphical interface at all.  I can only get to the intial sign in by line command.  I can then sign in but I am still at the line command tty terminal.
 
Mark

---

### Post by MatadorMac on 2010-07-12
> **oldfred said:**
> I have nvidia, but saved this link. Not sure if it is current or not.
 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
okay, followed that thread URL and then onto another through that that might work.  I am working on this now and will post my results when I have any.  In the mean time, any more suggestions are always welcome.
 
Mark

---

### Post by MatadorMac on 2010-07-12
> **MatadorMac said:**
> okay, followed that thread URL and then onto another through that that might work. I am working on this now and will post my results when I have any. In the mean time, any more suggestions are always welcome.
 
Mark
 
Well, things seem to be a bit closer to working but I can still not get past the UBUNTU screen to the graphical log in.
 
Is there a way to invoke a 10.04 system recovery which does not destory my documents and installed programs?
 
Regards
 
Mark

---

### Post by oldfred on 2010-07-12
From the grub menu can you boot the recovery mode that should take you to  a command line? It does not use the video drivers to start.

---

### Post by MatadorMac on 2010-07-12
> **oldfred said:**
> From the grub menu can you boot the recovery mode that should take you to a command line? It does not use the video drivers to start.
 
Yes, eventually I can get there but I don't really know what to do there.  I did delete and then re-install the video driver and that seems to have improved the screen resolution. BUT, I can't boot into the UBUNTU graphical interface or figure out what to do next.
 
Can I do a repair of my Ubuntu 10.04 installation without endangering my installed programs or documents?
 
Thank you
 
Mark

---

### Post by oldfred on 2010-07-12
From command line this will try to start gdm:
sudo service gdm start

To update from command line if that is where you are at:

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

If you have to configure your video I do not know how to do that.

---

### Post by MatadorMac on 2010-07-13
> **oldfred said:**
> From command line this will try to start gdm:
sudo service gdm start
 
To update from command line if that is where you are at:
 
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
 
If you have to configure your video I do not know how to do that.
 
 
 
:)  Well that seems to have fixed some things but I am still stuck at not being able to pass the "low screen resolution" window.  It just sticks when I wait and when I click the "OK" it takes me back to the command line interface.
 
I am stuck and perhaps need to think about a broader recovery.  I wonder if I started from CD image of Ubuntu whether that would work or not.
 
Than kyou
 
Mark

---

### Post by MatadorMac on 2010-07-13
Okay, a bit further now.

I was still stopped at starting the graphical user desktop.

Then I tried to start gdm as a program and was informed that "it wasn't installed!!"

So, I installed gdm, rebooted and got to my usual UBUNTU log in screen.  After logging in the desktop stopped and a white square appeared in the upper left corner of the screen with a line command terminal.

I can't log further into gdm, it says it is running but I don't get the normal graphical desktop.  Again, I am stumped as to what to do further.

Suggestions?  I do feel I am getting closer.

Mark

---

