---
title: "I'm confused with partitioning"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by DaveGiant on 2008-02-02
I have a mac which has been sliced into 3 partitions using bootcamp and the the disk utility.

OSX is on my main partition.
XP is on my smallest partition.

I have created a medium sized partition for Ubuntu to run on.

I run the installer and get to the 'prepare disk space' screen. Manual seems like the safest way to go considering my setup.

I click on manual and continue. I select a tiny partition and make into a swap partition. I then select the medium partition. I select FAT32. I am then asked for the mount point. I have a choice between dos and windows. However the partition is just a blank partition and neither apply. I have tried both adn forward. Tried nothing and forward. Nothing works. I keep getting the message.

'No root file system is defined.'

How do I get around this?

---

### Post by Vadi on 2008-02-02
Make the mount point be

/

(yes, just a forward slash)

Edit: Btw, you should select ext3 for Ubuntu.

---

