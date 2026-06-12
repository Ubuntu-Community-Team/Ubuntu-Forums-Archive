---
title: "Post karmic upgrade and my canon LBP 8IV isn't working"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skippergimp on 2009-10-21
I have upgraded to karmic and my laser printer isn't working.  My colour printer is okay so CUPS can't be 100% broken.

The printer is connected with a PCI parallel card as the mobo has no parallel port.  The printer stills functions when I use it via my laptop and its parallel port.

The printer is reachable by the system as it sends the test page but the resulting page is garbage.  The driver I am using is the lbp8 foomatic driver and not the recommended foomatic cjet driver.  This driver has always worked for over the course of numerous dostros.

During the upgrade, it asked if I wanted to replace the existing cups config and I said yes as I couldn't remember making any changes to the setup that would be lost.  I have had a little look in /var/run/cups to see if there is an old config file and there doesn't appear to be.

So far I have tried the cjet and lbp8 drivers for the LBP 8A1 which has always been close enough to work until now.  I have also removed cups and reinstalled it to make sure there was no corruption in the install.

Any pointers as to what to try next?

Whenever I send the test print page, the printer beeps, something it never used to do.  So the printer is registering some kind of error to trigger the beeps

---

### Post by skippergimp on 2009-10-21
Just to make sure, I have removed the card and put it back in to make sure it was a loose connection connection causing my problems.

---

### Post by skippergimp on 2009-10-22
Is anyone else having a CUPS problem post karmic upgrade?

---

### Post by skippergimp on 2009-10-22
I have just tried the 9.04 love CD for Ubuntu and can confirm that the hardware works fine.  It does seem the problem lurks in Karmic somehow.

---

### Post by skippergimp on 2009-10-23
If the Live CD for 9.04 gives me a working printer but my Karmic upgrade has broken, how could I go about copying the 9.04 CUPS config into Karmic?  Could I get away with changing the repos to the live CD and install CUPS etc from there?

---

### Post by skippergimp on 2009-10-25
I have downloaded the Karmic RC iso and tried that as a live disk and no joy.  Still the same printer problems. Karmic seems flawed for me. So I have backed up and re-installed 9.04 and won't be upgrading again anytime soon.

---

### Post by skippergimp on 2009-10-26
As the problem appeared to be in the Live CD, I tried to file a bug report in Launchpad.  After 30 minutes of trying to find the Submit a bug report link and searching for EASY to read help, still no luck in filling a bug report.  

As I can't actually file a bug report, it looks that it is never going to be fixed, so bye, bye karmic.

---

