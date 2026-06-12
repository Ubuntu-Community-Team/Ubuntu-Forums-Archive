---
title: "Syncing a Sony Clie palm"
date: 2008-09-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forrestcupp on 2008-09-09
I'm using an updated version of Intrepid.  I'm trying to get an old Sony Clie NX70V to sync, and I'm not having any luck setting it up.  I can tell that Ubuntu *is* recognizing the Clie, but I can't get it to connect.

Here is the output of lsusb while the hotsync button is pressed:

```
Bus 006 Device 007: ID 054c:00da Sony Corp. Sony Clie nx60
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c20b Logitech, Inc. WingMan Action Pad
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 04ca:0020 Lite-On Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```So you can see the Clie on the first line being recognized.  I just can't figure out which device to use; I've tried all of them listed in the setup.  Here is the diff of my /dev directory when the clie is turned on and off:
```
693a694,698
> usbdev5.37_ep00
> usbdev5.37_ep02
> usbdev5.37_ep07
> usbdev5.37_ep81
> usbdev5.37_ep86

```The number 37 increments each time I turn the device on.

From other posts I've found, I've also tried adding visor to the modules.  That didn't help.

I really thought Palms were supposed to be easier to set up in Linux than PocketPC's.  It's recognized, but I can't get it to connect.  Does anyone have any ideas?

---

### Post by forrestcupp on 2008-09-10
I may be getting closer.  I realized that the Palm rule in /etc/udev/rules.d/60-symlinks.rules wasn't creating the symlink called /dev/pilot.  I found a fix for that [here](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg09355.html).  So I commented out that rule and put the following in its place:
```
KERNEL=="ttyUSB*", SYSFS{product}=="*Palm*", \
					SYMLINK+="pilot"
```

Now it successfully creates the pilot symlink whenever I press the hotsync button.  But it still is not connecting to Gnome Pilot.  It just keeps trying to connect until it finally times out.  That is using the USB option.  If I try leaving it on Serial, it tells me I don't have permission.

I am using the visor module.  Does anyone have any ideas?

@admins & staff - if this thread would be better somewhere else, would you please move it for me?

---

### Post by ArgentSilver on 2008-09-14
I posted this info elsewhere today, but looks like you need it too!

Under Hardy, I found that you don't need the visor module or any changes to the symlink rules. Basically you have to tell your sync software to find your Palm device at "usb:" (without the quotes) and NOT at /dev/pilot or /dev/ttyUSBx.

---

### Post by forrestcupp on 2008-09-15
How do you do that?  In Gnome Pilot where it has the drop down box to choose where to find the Clie, I had already tried typing in **usb:** in that space.  It didn't work, either.  And I did try that without visor and with the normal symlink.


Edit:
I just tried it again.  I removed visor from the modules, and I reverted back to the original symlink setting.  Then in gnome-pilot, I typed **usb:** into that box.  It still timed out and didn't work.

---

### Post by ArgentSilver on 2008-09-15
Sorry I can't help you with Gnome pilot. I'm using KDE so I was using Kpilot, and there you just go into the configuration and tell it to find the Palm at usb: instead of /dev/pilot.

My base setup has the visor module blacklisted in /etc/modprobe.d/libpisock9 (it came that way) and an unmodified udev rules.

---

### Post by forrestcupp on 2008-09-16
Thanks for the info.  If I can't get gnome-pilot working, I might end up trying kpilot.  I'm also reinstalling Hardy to see if it happens to be a problem with Intrepid.

Thank you.

---

### Post by forrestcupp on 2008-09-17
Well, I couldn't even get it working with kpilot in Hardy.  When I tried to set it up it gave a warning about Sony Clies.  Maybe it's just time to retire the old thing.

---

### Post by ArgentSilver on 2008-09-20
Sorry to hear you're still having trouble. The only other suggestion I can make is to try going to the command-line. If you install pilot-link you can try this:
Connect your Clie to a usb port.
Type the command but don't yet push <Enter>.
pilot-xfer --port=usb: -b /YourChosenDirectory

Then push the hotsync button on the cradle/Clie... and then push <Enter>.

If it works, this would completely backup all files on the Clie to the directory shown. Then to install a file it would be:
pilot-xfer --port=usb: -i somefile.pdb

This also works for my TX under Kubuntu Hardy, so maybe it would work for you... Good luck!

---

### Post by Foaming Draught on 2008-09-20
I assume that it's Evolution you're trying to sync with?

Waste of time.  If the Clie is important to you (my Palm is to me), then ditch Evolution, it will never sync reliably, and use JPilot for your PIM and Thunderbird, Opera or webmail for mail.

sudo apt-get install pilot-link jpilot

Also sudo apt-get install jppy if your Clie OS is 4.0 or newer 

In JPilot File/Preferences/Settings/Serial Port, enter usb:

Press the hotsync button on the Clie's cradle, then hotsync on JPilot, and it syncs flawlessly and reliably.

---

### Post by Nizarus on 2008-10-12
I have the same issue with my clie
the device is recognised by the system (lsus) but not recognised by gpilot !!

---

### Post by Nizarus on 2008-10-14
I added a bug report : [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-pilot/+bug/282491](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-pilot/+bug/282491)

---

### Post by GlennW on 2008-10-20
forrestcupp and Nizarus!

I was just given a Clie TJ25 from a friend who's always up on the latest toys so I got this hand-me-down. I did a bit of reading and found that the default gnome-pilot is pretty much useless cruft. 

I installed J-Pilot using synaptic. Then after reading this thread, realized that under the J-Pilot preferences>settings>Serial Port I had to enter usb: in the input box. 

I closed J-Pilot down connected my Palm, opened up J-Pilot and hit sync and wa-la! Connection!

Give that a try!

Cheers...

---

### Post by froghopper on 2008-10-20
The current version of gnome-pilot in intrepid is broken due to changes in hal. See here [http://bugzilla.gnome.org/show_bug.cgi?id=484509]("http://bugzilla.gnome.org/show_bug.cgi?id=484509")

You can stop hal with this command:

sudo /etc/init.d/hal stop

then restart the gpilotd daemon with the panel icon and you should be able to perform the initial sync.

---

