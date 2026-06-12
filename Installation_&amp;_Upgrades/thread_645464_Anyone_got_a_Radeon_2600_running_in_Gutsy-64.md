---
title: "Anyone got a Radeon 2600 running in Gutsy-64?"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by Applegeek on 2007-12-20
Can anyone throw me a bone here?

Trying to install Radeon HD 2600 Xt.

Clean install Gutsy amd64 on an Athlon X2 4600 system.  Vesa drivers kind of work, but very slow, wrong resolution.

Read up on AMD/ATI drivers.  Downloaded latest installer from ATI, ran it according to instructions.

Rebooted machine, and ran aticonfig --initial.  The xorg.conf gets updated and show fglrx driver.

Rebooted machine.

Try to run compiz --replace.

Tells me Xgl not present, driver not whitelisted.  I whitelist the driver and install Xgl server.

Reboot and run compiz --replace.

It'll either try to start copmiz and run really, really slow, or just go to white screen.

Can anyone please give me a clue as to what's going on here??  This shouldn't be this hard to install a video card...

Is there a good how-to to get a Radeon 2600 actually to run under Gutsy??  :confused:

UPDATE:  Found this thread: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  

It looks like I haven't played with the Option "Composite" "False" yet...And I have to un-install the Xgl also.

What a cluster ^&%...Reminds me of Windoze...

---

### Post by igknighted on 2007-12-20
The 2600 cannot use the community driver.  There are a couple open-source drivers on the way, but they do not support 3d at this time (radeonhd is the most promising... ati/amd is helping to develop this).

When using the fglrx driver, since you used the latest from amd.com, composite support should be enabled, I don't think you need to use XGL.  That is probably more of a pain than it is worth.

---

### Post by Applegeek on 2007-12-20
Ok, how does one enable composite support...

Is this changing  the

Option "Composite" "0"

I have in the Extensions section of xorg.conf?

This is really getting to be a pain in the neck...

---

### Post by igknighted on 2007-12-20
Changing the '0' to and '1' or 'enable' should do the trick.  I would recommend searching for a guide though, because there are bugs that could come up.  I no longer use ATI, so I can't tell you for sure what they are, but I would think there would be a pretty prominant guide somewhere on here.

---

### Post by Applegeek on 2007-12-21
FINALLY!!  THE RADEON 2600 CARD WORKS REALLY SWELL NOW!!

:):):):)

Gotta follow this step - by - step on the manual method 2

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

You start by removing EVERYTHING related to anything you tried before.  Clean out your xorg.conf, or better yet erase it and rebuild with:

sudo dpkg-reconfigure -phigh xserver-xorg

Remove Xgl drivers.  Remove any other ATI video drivers on your system.

DO NOT use the restricted driver setup from the repository, it is out of date.

On the link above use Method 2 - Manual Install for Gutsy.  It is a very good guide, much easier to follow than the guides here...Not complaining, just a fact.

Important notes to remember - Don't use XGL with the new ATI driver, and "Composite" option is already on by default with the new driver.

After I followed the above to a "T", everything is running and The Cube is spinning nicely with the Radeon HD 2600 XT under Gutsy.

This would be too tough for ordinary users to go thru each time they wanted to install a video card - these are the kinds of area in Ubuntu (and Linux in general) the are in serious need of simplification.

But in the end, it all works - and even though the Radeon might be a stitch slower than its Nvidia counterparts, it offers a better display of live video and color balance to my eye.  It seems to have a bit better anti-aliasing and noise reduction, and a bit more suited to HTPC systems.

Yahoo!!

:):):):)

---

