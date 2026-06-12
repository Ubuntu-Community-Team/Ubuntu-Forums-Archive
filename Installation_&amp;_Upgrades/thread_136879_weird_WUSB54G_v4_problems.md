---
title: "weird WUSB54G v4 problems"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by billylh on 2006-02-26
Thanks to this forum, I've been able to get my WUSB54g v4 adapter working with Ubuntu 5.10 Breezy, but I've noticed that as soon as I leave the computer for a couple of minutes, the adapter seems to go to sleep and doesnt work again until I reboot the system.  I imagine that there is some setting for it to not go into sleep mode? but to stay constantly connected to my AP.  I just find it very annoying and time consuming (since I run it on a fairly slow system.) to have to reboot everytime.  Is there something I can do about this?  
TIA,
Billy

---

### Post by pestilence4hr on 2006-02-26
Don't know about the "sleeping" issue, but I'd venture to guess that if you remove and re-insert the module for your adapter, it will wake up... once you know the module name, try "sudo rmmod <modulename> && sudo modprobe <modulename>"

---

### Post by billylh on 2006-02-27
could this be an issue witht he driver i used?  i used the rt2500usb.inf file from my linksys disc.  is there a better driver i should use ? and if so, where i can find it?

---

### Post by Paperfolder on 2006-02-28
Billylh and venerated moderators,
           I'm completely new to Linux and Ubuntu but have been struggling with W**ndows for 12 years. I've installed the Badger on a standalone PIII machine and am delighted with the new desktop.  I'm anxious to start exploring but do not yet have my internet connection.  I have a WRT54G router and a windows machine connected wirelessly.  I'd like to connect the Ubuntu box wirelessly but have no idea how to proceed.  I have a PCI Adapter, the WMP54G and need your help to get me going.  Any direction you could give would be gratefully appreciated.

Thanks,
folder

---

### Post by pestilence4hr on 2006-03-03
I don't know the answer to your question, Billylh, but if you followed the instructions at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)  under WUSB54Gv4, then I don't have anything else to tell you.  Note, they seem to have to load ehci with modprobe ehci-hcd log2_irq_thresh=4 to avoid some errors, possibly the ones you are having.

---

### Post by pestilence4hr on 2006-03-03
Paperfolder, I would suggest you start your own thread.  You'll have a much better chance of finding somebody who wants to help.

---

