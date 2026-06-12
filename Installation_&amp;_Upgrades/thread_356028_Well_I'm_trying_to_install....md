---
title: "Well I'm trying to install..."
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by penguin957 on 2007-02-07
Well when I boot to the Ubuntu CD I have been pressing "Start or install Ubuntu."  When I do this it says the following:
*Activating swap...
 mount: Function not implemented
*Checking file systems...
fsck 1.39 (29-May-2006)

Then it pops up that it "Failed to start the X server (your GUI).  It is likely that it isn't set up correctly.  Would you like to view the X server output to diagnose the problem?

I checked to see if there were any problems with the disk and there were none.  I guess I'm just doing something wrong (probably a stupid mistake).

---

### Post by penguin957 on 2007-02-07
I forgot to add my system specs (they aren't that great anyway haha):

CPU:  Intel Celeron 2.4 Ghz
Monitor: LCD
Ram Amount: 1 gig
HD: 250GB IDE
Graphics Card: Nvidia 5500OC 
Broadcom 10/100 Ethernet Card
and I'm trying to Install version 6.10

---

### Post by mikewhatever on 2007-02-07
You've done nothing wrong penguin. As the error message said, X server is the graphic interface, that was unable to start. Usually, it happens because of problematic video cards, such as ATI.
To solve this, you may need to get the Alternate install CD from the download page. Alternate CD is a text mode installer with no fancy graphics, so hopefully, you'll be able to install, and then deal with X server if needed.
There is a [Good Guide]("http://users.bigpond.net.au/hermanzone/") on how to use the text mode installer. If you do not dual boot, just disregard whatever is says about Windows.
Here is [X server]("http://users.bigpond.net.au/hermanzone/p7.html") page from the same guide.

Good Luck

---

### Post by penguin957 on 2007-02-08
Thanks for the help!  I'll look at all that tomorrow since I have an 8 o'clock class.

---

