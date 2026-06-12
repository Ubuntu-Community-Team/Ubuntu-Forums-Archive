---
title: "Here's what I did"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by suchnsuch on 2005-03-15
With all of these people here, I'm sure that I'm not the only one to run into this.  Hopefully someone can help me oput here.  Here's what I did, and what happened:

1.   I loaded V4.1. 
2.  System prompts you to remove cd and reboot
3.  system reboots
4.  After a few bios setting changes I get past the **grub** screen
5. Then, it runs through a bunch of startup text where I get some **modprobe: FATAL: error . . . . .etc.etc**. messages for **pciehp**, **shpchp**, and **hwrandom**  *(From what I've found here these are common messages and should not be fatal?)*
6.  Now I'm expecting a login screen, but I get a screen that is blue on the top half of the screen, and black on the bottom half of the screen, and in the upper left corner it says "**ubuntu configuration**"
7.  Then, nothing. . . .

Im not doing a dual boot system.  Ubuntu is the only OS installed.  I only have 1 hard drive.  I'm using an ASUS P4B mother board, and a FireGL4 graphics card.  None of my devices are USB.

Anyone have an idea of what I might try next?  I'm really dead in the water.  Thanks-

---

### Post by suchnsuch on 2005-03-15
found this:
$ sudo cp /etc/hotplug/blacklist /etc/hotplug/blacklist_backup
$ sudo gedit /etc/hotplug/blacklist

But, how do I get to a command prompt if the system hasn't finnished booting?

---

### Post by suchnsuch on 2005-03-15
Yeah, me again.  In the above post, this is the screen I am expecting when everything locks up.
[http://shots.osdir.com/slideshows/156/11.gif](http://shots.osdir.com/slideshows/156/11.gif)[http://shots.osdir.com/slideshows/156/11.gif](http://shots.osdir.com/slideshows/156/11.gif)

---

### Post by Cybermagellan on 2005-03-15
If your having problems after the standard installation then you might wanna redownload/burn your image. I think at this point the installation is still running from the CD copied .debs so everything it's installing from at this point is HD based (I could be wrong).

---

### Post by Gary Powers on 2005-03-15
Have you tried to reinstall?  If it repeats the problem, might be worth burning a new install CD.  If there were an error in your install disk, it might be very difficult to find.

Gary

---

### Post by Martin Witte on 2005-03-15
I do get the same modprobe errors, it tries to load some stuff for the usb ports at this point - and this fails. For me this is not fatal.
Initially I also had a vague screen like you - for me it turned out the video was not installed correctly. I fixed it by first install the vesa driver (I have a Sis chip), at a resolution which worked I knew what can work for me (I found this out using the Knoppix bootable  cd-rom).
At this point a downloaded the latest driver - for me this was via [http://www.winischhofer.net/index.shtml](http://www.winischhofer.net/index.shtml) - and configured that with sudo dpkg-reconfigure xserver-xfree86.
Hope this helps, Martin

---

### Post by suchnsuch on 2005-03-17
well I used three different cd's burned from each of my other 3 cd burners, so I think I can eliminate the idea that it may be a bad cd.  Still cant get past the blue screen of death.  (this was a new disk, never even had another OS on it?)  I can only think of one other thing that may be causing the boot to fail before I get the the configuration screen.  The system flashes something about networking on the screen for 1/100 second before going to the dead configuration screen.  Do you think there could be a networking issue that is stoping the boot?  During the install proccess I dont get any errors about the network, it seems to locate it and connect properly.  Am I really the only one this ever happened too?  Come on, help a guy out here would ya?

---

