---
title: "ATI dual monitor issues (Karmic)"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Spoonlord on 2009-10-09
Im running into issues with my monitor setup, ive had similar issues with 9.04 previously but these were solved by installing the AMD supplied drivers rather than the ubuntu supplied one. However having had problems in the past with distro upgrades with those I want to keep to the ubuntu ones for now if possible.

My setup is as follows

One Samsung 23" attached by DVI/HDMI
One Xerox 19" attached by DVI
The video card is a Radeon 4870 1gb card
Using the current Karmic build fully updated and the fglrx drivers

My problem is that I cannot get both displays to run properly in native res and in digital

Currently the displays are shown in Display preferences as:
SAMSUNG 23" (perfectly working on dvi)
Unknown (looks like the analog input on the Xerox)
XER 19" (The digital input on the xerox)

If I enable the Xer monitor and disable the Unknown one in the display preferences it asks to re-log, and nothing happens.

the ATI CCC wont allow me to select the digital output at all athough it lists it.

Basically I think I need to disable the Unknown monitor. Any help would help.

---

### Post by Spoonlord on 2009-10-09
Also I nearly forgot despite it being in front of me, the 19" xerox when enabled (it shows as screen one in CCC but is on the left and not the main screen) flickers now and again (which I think is more to do with the crappy VGA support it has), and athough I can move the mouse cursor around the entire screen, the desktop only takes up the left couple of inches, rest of the screen is black. (although I can still drag stuff into the area I can't see).

---

### Post by QIII on 2009-10-10
You may not be aware that AMD/ATI has a new driver version 9.10 (they skipped right over 9.9 to get 9.10 ready just in time for Karmic).

Check this out:

[http://blog.linuxniche.net/?p=447](http://blog.linuxniche.net/?p=447)

You should also read:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by Spoonlord on 2009-10-10
I'll check those out now thankyou

---

### Post by Spoonlord on 2009-10-10
Looks like I am running the 9.10 fglrx driver, and I don't really want to patch the 9.9 drivers which did work for me :/

Its annoying really since the driver work perfectly apart from these problems.

---

### Post by QIII on 2009-10-10
Hmmm...

Neither of my Karmic test machines has an ATI GPU, so I can't test out the new driver.

When I install Karmic on my "everyday" machine, which does have an ATI GPU, I'll plug an old monitor in the VGA head and see if I can get two monitors to work.

---

### Post by Guy Sibley on 2009-10-10
So can I take from this that the normal ATI radeon HD drivers are working (at least to some degree of acceptability) in Karmic?

---

### Post by QIII on 2009-10-10
What can be taken is:

1.  ATI has decided to catch up to nVidia in terms of driver support for Linux.

2.  ATI skipped over version 9.9 for the moment to get 9.10 ready for Karmic (and, by the way, only for Karmic.  The other distros may have to wait for a more tailored driver.)

3.  From all the reviews I have read, it seems to finally fit the bill.

As I said, neither of my Karmic machines has an ATI GPU, so I can't render my own assessment.

---

### Post by Spoonlord on 2009-10-11
Apart from my strange second monitor issue, yes I would say they are fine. Acceleration is working perfectly as far as I can tell and stability has been fine.

working on some work-arounds on my machine to fix my issues, will report back ;)

---

### Post by Spoonlord on 2009-10-12
It works!
OGL acceleration is in place and working.

what I did:

Reinstalled 9.10 completly
installed ALL updates before attempting ati driver installation (this took a reboot or two to be sure, and also enabling of some held back packages (Not sure why they were))
another reboot
then I found bit of a school boy error that I had to disable the Analog monitor** THEN** enable the digital meh, looks like 4870 just plain ignore commands rather being helpful when in this situation.

My Part screen issue disappeared on the re-install, I assume some kind of patch fixed that issue.

Helpful notes: 

Xinerama stops compositing. Meh.
VGA output was very flaky for me, flicking and such, may be because of the mixture and the questionable quality of the VGA component of my monitor.
If you need to move your Gnome Panels, remember you have to hold down the left alt key now.

---

### Post by markbuntu on 2009-10-12
I had no problems setting up my 2 gpus and 3 monitors with fglrx in karmic. it was a lot easier than with previous drivers. It disables randr automatically when you select single desktop for multiple monitors for one thing. It is still a little tedious having to restart after each change.

The ximerama no compositing thingy for multi gpu has to do with the move to randr which had no multi gpu support until the latest release which will not make it into karmic. So we should be able to say a final goodbye to xinerama and get compositing back for our multi gpu setups when the drivers and distros catch up over the next release cycle.

If you only have one gpu with one or two monitors you should not have any problems with fglrx.

---

