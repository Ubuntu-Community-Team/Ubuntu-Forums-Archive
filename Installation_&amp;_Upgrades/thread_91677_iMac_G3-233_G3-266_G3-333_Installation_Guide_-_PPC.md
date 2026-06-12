---
title: "iMac G3-233 G3-266 G3-333 Installation Guide - PPC"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by mrrabbit on 2005-11-17
Hardware Preparation

Upgrade the iMac G3-233/266/333

-  Purchase PC100 SO-DIMMS that sellers guarantee will work with the iMac G3.  This is especially important when using 256M SO-DIMMS.  Not all PC100 SO-DIMMS are the same - some 256M SO-DIMMS will be seen as only 128M SO-DIMMS.  I recommended upgrading to at least 256M and to 512M for a full install or development/rendering oriented machine.  THESE MACHINES MAX OUT AT 512M RAM.

-  Upgrade to at least a 10G IDE hard drive as a means for accomodating later package installs and user data.  KEEP THE RPM AT 5400 MAX!!!  The only fan in the iMac serves the monitor and the motherboard/memory/drive module.  Going with a 7XXX may cause overheating - 10,000 RPM drive will cause overheating.


Unbuntu 5.10 Live CD Startup - PPC

To keep Ubuntu from freezing just before the login screen of a GNOME login after everything has loaded:

1.  Deselect DRI when presented with the X modules list.  Respond with "NO" to writing DRI module information to the X config file.

2.  For pretty much everything, go with defaults...including preseeded answers...


Unbuntu 5.10 Installation - PPC

The install CD works very well.  Boot up the CDROM and then choose to do a TEXT BASED EXPERT INSTALL.  I don't remember the exact label, hit TAB to list the boot labels - choose the one needed.

If prompted for any of the parameters dealt with in the Live CD section, repeat them.

Do give yourself 256M to 512M swap and a decent / partition size - mine was 7 Gigs.  If you like separating out /opt, /usr and the like, suit yourself.  Make sure your partitioning has an Apple Bootstrap partition.

MAKE ABSOLUTELY CERTAIN YOU CREATE A NORMAL USER ACCOUNT!!!

Kick back, enjoy your coffee - there's even time for your SO.  It will take 1.5 to 2.0 hours.  Plenty of time if you know what I mean...


Post-Install Adjustments


Adjustment A

Login with the normal user account.  Immediately find and open the Volume/Sound Mixer control panel.  Enable headphones.  Turn off the microphone.

From here onward, when using one, always turn off the other.  Having the headphones/speaker AND the microphone on at the same time will result in feedback when raising the volume.


Adjustment B

Open a terminal window.  SU to root.  Edit /etc/gdm/gdm.conf...

Find the line that has "false" set for local root login and set it to "true".  Exit the terminal and then reboot.

After rebooting login using the root account...and then open the Update Icon in the upper right tray to view and install available updates.  Most people will want to do this - one relates to SSL.

Go ahead and set personal system-wide configuration preferences while logged in as root.  Decide for yourself when to disable GNOME root login.


My overall evaluation of Ubuntu 5.10 - PPC.


I am very impressed.  Fedora Core 4 failed - the stupid partitioner script in the install formats the bootstrap partition as ext3.  POOF went Yaboot.  DOH!!!

Debian seemed the way to go...however first install screen in expert and text mode...FREEZES!!!

YellowDog...$$$$$$$$

...however, don't pat yourself on the back too fast Unbuntu team...one criticism follows....


...don't label your distribution and promote it in such a touchy-feely everyone sing "Kumbaya" fashion....and then have the following comment in /etc/gdm/gdm.conf:

Paraphrasing:  "Anyone who enables root login in Gnone should be shot!"

If you are going to insist on that, then be consistent.  Rename your distro "Udietu" and promote it as a distro for the elitist and opinionated who desire death for everyone else...

Take it from a hardcore Michael Savage type independent conservative like myself:  

"Warn, persuade, but otherwise leave it up to the end-user to decide whether they want to cut themselves off at the knees or not."


Sincerely,

Robert Shackelford
New Ubuntu Tester

=8-)

---

### Post by yesplease on 2005-11-18
>  ...however, don't pat yourself on the back too fast Unbuntu team...one criticism follows....


...don't label your distribution and promote it in such a touchy-feely everyone sing "Kumbaya" fashion....and then have the following comment in /etc/gdm/gdm.conf:

Paraphrasing:  "Anyone who enables root login in Gnone should be shot!"

If you are going to insist on that, then be consistent.  Rename your distro "Udietu" and promote it as a distro for the elitist and opinionated who desire death for everyone else...

Take it from a hardcore Michael Savage type independent conservative like myself:  

"Warn, persuade, but otherwise leave it up to the end-user to decide whether they want to cut themselves off at the knees or not."


Sincerely
Robert Shackelford
New Ubuntu Tester

=8-)

Finally robert Shackelford became a New Ubuntu Tester! Great, I am sure the Ubuntu developers are laying down their work until the test reports arrive. Give them a chance to repair their errors and please dont shoot anybody in the mean time. ;)

Edit: I forgot to mention that is nice of you to make a guide for the iMac.

---

