---
title: "Why so many entries in Gnome-Session?"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by groggyboy on 2008-10-03
I opened up Gnome-Session today to add an entry for startup, and I noticed a long list was already there.  There are, by default, 20 programs at startup (plus four i've added)!  I'm running Intrepid, by the way.  I seem to recall back in the breezy badger days that there was only a small handful of entries there, and with every new release of Ubuntu, that list has grown.  Are these all nescessary?

**1.** AT SPI Registry Wrapper - what does this even do? I've disabled it to no ill effect.
**2.** Bluetooth Manager - I have no bluetooth on my laptop, so I disabled this one.
**3.** Check for new hardware drivers - after first boot, when this produced nothing, i disabled it.  I have pretty standard intel hardware anyways.
**4.** Evolution Alarm Notifier - i don't use evolution, so it's been disabled.
**5.** GNOME Keyring Daemon Wrapper - sounds important, so I left it enabled.  after all, network-manager accesses the keyring (as well as some other programs).
**6.** GNOME Login Sound - I've disabled this.  Does it have something to do with pulseaudio or libcanberra?
**7.** GNOME Settings Daemon - I left this alone because it sounds important.
**8.** GNOME Settings Daemon Helper - Same as above.  Can anyone shed light on these two entries?
**9.** GNOME Splash Screen - I disabled it. Ubuntu doesn't use a splash screen after login, so why is this even here?
**10.** Network Manager - Well, I have a laptop, so unless I switch to WICD, i'm keeping this.
**11.** Power Manager - Again, I have a laptop, so I've left this one alone.
**12.** Print Queue Applet - Pretty obvious what this is for.  I've left it enabled.
**13.** PulseAudio Session Management - At an educated guess, this is for pulseaudio.  I like music, so I've left this alone.
**14.** Remote Desktop - Again, pretty clear what this is for, but I only have one computer and I don't use vinagre, so I disabled this.
**15.** Tracker
**16.** Tracker Applet - I don't use tracker or beagle because I keep my files organized, so I've disabled these two.  Besides, I find tracker to be a memory and storage hog.
**17.** Update Notifier - I know what this is, and I've left it enabled.  Updates are good.
**18.** User folders update - I figured out that this is what creates all the folders in my home directory (like Music, Documents, Public, Templates, etc).  I have my home directory set up how i want it, so this is a nuisance.  I don't want a Public folder.  That's why i deleted it.  Disabled.
**19.** Visual Assistance - This must be for assistive technologies.  I don't need it, so it's disabled.
**20.** Window Manager - What?  I can't for the life of me figure this one out.  I thought gnome had a built-in window manager (metacity). I've been having problems with compiz not starting at login.  Could this be causing that?  I'm leaving it enabled until I learn more.

Plus, I have four entries of my own:
**1.** AWN - cuz it's pretty.
**2.** GNOME-Do - again, cuz it's pretty (and useful).
**3.** Fusion-Icon - i'm using this because compiz isn't starting properly for me - could it be related to the final entry from above?
**4.** PulseAudio Device Chooser - I like having the applet in my notification area so I can play with some of pulseaudio's neater functions.

That's 24 entries!  Granted, only 13 of them are enabled on my computer, but that's still alot.  Couldn't this be streamlined?  Are they all nescessary (i'm looking at GNOME Login Sound, GNOME Splash Screen, and User folders update)?  And what are the more arcane entries even for?  Thoughts, anybody?

---

### Post by olskar on 2008-10-03
Starting to sound like windows :)

---

### Post by syko21 on 2008-10-03
> **groggyboy said:**
> 
**20.** Window Manager - What?  I can't for the life of me figure this one out.  I thought gnome had a built-in window manager (metacity). I've been having problems with compiz not starting at login.  Could this be causing that?  I'm leaving it enabled until I learn more.


If compiz ever fails on you this will trigger the gnome window manager. I tried running metacity --replace and it didn't work for me when i had a driver mess up.

---

### Post by vishzilla on 2008-10-04
I disabled GNOME login sound. Pulseaudio kept breaking my sound. After disabling it, my sound doesn't break.

---

### Post by MaX on 2008-10-04
> 1. AT SPI Registry Wrapper - what does this even do? I've disabled it to no ill effect.
"The Gnome a11y infrastructure allows end user assistive
technology (AT) programs such as screen readers to get rich
information about an application's UI state. Application's use the ATK
library to serve information but for stock GTK+ widgets the GAIL
library does this automatically when the Gnome Accessibility option
for Enable Assistive Technology is turned on. ATs access the
information via AT-SPI protocols (Corba based). KDE are now looking at
implementing it as well and IAccessibility2 extends Microsofts MSAA to
be very similar semantically."
[http://mail.gnome.org/archives/gnome-accessibility-list/2007-May/msg00010.html](http://mail.gnome.org/archives/gnome-accessibility-list/2007-May/msg00010.html)

---

### Post by plun on 2008-10-04
> **olskar said:**
> Starting to sound like windows :)

Black Viper can start a new Gnome settings area...:D

[http://www.blackviper.com/](http://www.blackviper.com/)


It causes a lot of trouble if unexperienced users starts to
disable default configurations...

Windows experience...:-\"

---

### Post by vishzilla on 2008-10-05
today i looked up in system monitor. oh god, intrepid uses about 48-50% of memory on startup. with hardy it ranged from 35-40% of my 512 MB RAM. i'm disabling unnecessary processes.

---

