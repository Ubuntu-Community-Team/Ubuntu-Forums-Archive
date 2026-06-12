---
title: "Install not installing...."
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by socrref on 2006-12-01
I'm trying to install Edgy on an old Dell: 930MHz, 128MB memory, 20GB disk (15GB free).  CD appears to boot OK, get message to "Start or Install Ubuntu."  I click on this option and CD apparently tries to actually start rather than install.  I found a link that describes the install process, detailing the options for disk partitioning.  My system never displays that.  I do get a message that something is not right with GNOME daemon, but closing that window does not seem to stop anything.  Finally ends up with Ubuntu desktop with two icons -- Install and Examples -- neither one of which does anything when clicked.  Can anyone help?

---

### Post by Herman on 2006-12-01
Yes, you should use the 'Alternate' install CD in computers with less than about 256mb of RAM. See my sig link for how to use one of those.
Swap area becomes very important with that amount of RAM or less.
A small swap area (up to 1.0 GB) will help the Live CD to run on your system in the meantime, it you can create one somehow. Maybe try ([GParted -- LiveCD)]("http://gparted.sourceforge.net/livecd.php")
I have used the 'Alternate' CD many times to install in a computer with 128mb of RAM and Ubuntu will install and work okay in one. It used to take me about an hour and a half to install. There were only one or two things I had trouble doing. One of them was to use GParted when in is installed in Ubuntu when the swap area had to be unmounted with the 'swapoff' command. That used to slow the poor old thing to a near-frozen state. Other than that, Ubuntu should work okay in it.

Regards, Herman :D

---

### Post by socrref on 2006-12-04
Thanks for the info, Herman.  Alternate installation worked fine, although I ended up blowing away the Windows partition so I'm left with just Ubuntu.  That's OK but now the Netgear wireless NIC isn't working.  It was apparently found by installation and shows in the device list, but isn't connecting to the router.  I will get that sorted out when I have more time to play with it.  I'm also thinking of getting another RAM chip to speed things up.

Lloyd

---

