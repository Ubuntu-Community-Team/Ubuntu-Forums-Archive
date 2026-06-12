---
title: "Use USB Startup Disk for Fresh Install?"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2012-10-07
):P

I have made a startup disk on an 8 GB usb drive of Ubuntu 12.10 Beta 2.  
 

 I notice that the app I used is called "startup disk creator."  I had been thinking it was "startup disc creator." Is this (as a disk) still appropriate for installation (as the equivalent of a live cd)?
 

 I've tried to use it to implement a fresh install and,  so far, the install option just hangs at the window where I choose the installer to download 3rd party stuff while installing.

---

### Post by mikewhatever on 2012-10-07
The spelling shouldn't matter, if the installer hangs, something must be wrong with it. Try unchecking the 3rd party stuff - you can get it later. File a bug report, unless it's a known problem.

---

### Post by howefield on 2012-10-07
Yes, it is still appropriate for installation as the equivalent of a live cd. The issue is likely to be related to the development nature of the release you are using, ie 12.10.

---

### Post by Randymanme on 2012-10-07
BUMP

I originally had two questions for this thread, but thought it better instead to start two separate threads for two similar but separate questions.  One of the moderators, however, says that one of the questions is a duplication of the other, so here it is.

I have Precise Pangolin already installed and I would like to use the  USB Startup Disk of Quantum Quetzal to upgrade Precise Pangolin.  Is  this practical?    

I've tried adding the USB Startup Disk to software repositories via  Synaptic Package Manager, but it doesn't appear (I don't really think  that that's accurate, but it was something to try).

To make the question more specific, *if* I can use the  USB Startup Disk of Quantum Quetzal to upgrade a standing install of Precise Pangolin, [B]how do I do it?

[/B]  Right now my finances are rather limited; I'm trying to conserve use of  my last few DVD+Rs, and I'm using my Android phone for an internet  connection.  For some reason unknown to me, Precise won't upgrade in  place with APT.   (Maybe the problem could be that the bandwidth is too  small on my Android internet connection).

---

### Post by Topsiho on 2012-10-07
Indeed, as howefield already said, 12.10 is still in beta2, so is not fit for ordinary use. It stil may contain errors (eg. on two of my three computers, with Nvidia cards, I don't get a screenimage, one screen is totally black, and the other shows all kind of randomly colored pixels, on the third, a netbook, the screen is OK, but the mousepad doesn't work). Please only upgrade (if you really need to) to 12.10 when the definitive version is released, end of october.
And please note: 12.04 is supported for 5 years, until April 2017, 12.10 is supported for 18 months only, so get your calculator out and find that 12.10 is obsolete much sooner.

Greetz, Topsiho

---

### Post by Topsiho on 2012-10-07
You said:

"To make the question more specific, if I can use the USB Startup Disk of Quantum Quetzal to upgrade a standing install of Precise Pangolin, how do I do it?"

Well, that's easy: when the definitive 12.10 is released, in the update manager you'll find a button, that lets you upgrade, from 12.04, to 12.10 (unless you changed the settings).

Pressing this button (*** after fully updating your 12.04 first ***, in order to get a standard situation) the new updates of all your installed software (from the repositories) are downloaded and installed. No need for USB-sticks or LiveCD's at all. It may take a long time, depending on the software you have installed, downloading an equivalent of possibly several CDRoms and installing this may take hours. But it is easy, just clicking a button, and maybe having to answer one or two questions during the process, if you have bad luck.

With a low bandwidth connection this option seems hopeless to me, however.

Topsiho

---

### Post by Randymanme on 2012-10-07
Well said.  O:)  

Thank you very much to all.

I still get so excited over a new Ubuntu release that I figure (or more like, hope) that Beta 2 is close enough and that it won't be very long before I can update to the final release.

As always, all help and advice is much appreciated.

Thanks.

---

