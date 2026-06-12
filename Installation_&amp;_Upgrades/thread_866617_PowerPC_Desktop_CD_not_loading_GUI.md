---
title: "PowerPC Desktop CD not loading GUI?"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by felix_mc on 2008-07-22
I have a eMac from around 2004-ish with 1GHz processor, 1GB RAM and 32MB ATI Radeon 7500 graphics card. I have a 40GB 'free space' partition on my FireWire HD on which I want to install Ubuntu on. I downloaded and burned the latest version of the Ubuntu Hardy Desktop CD for PowerPC Macs.
It booted from the CD alright. It got to the part where [Ubuntu is loading]("http://www.dsl.sk/images/articles/2007-05-06-ubuntu-1.png"), but afterwards the screen just went black. I rebooted a few time time and the same thing happened. I'm guessing the GUI is failing to load because of some compatibility/configuration issues with the graphics card?
How can I fix this? I'm a complete Linux noob, though I've done some bash scripting under OS X.
Thanks for any help :D

---

### Post by komputes on 2008-07-22
I haven't played around with PowerPC's and Ubuntu, but I don't think it is officially or properly supported. I have had this issue before and I had to install Ubuntu from an Alternate Install CD instead of a Desktop Live CD, because of video issues. 

[http://cdimage.ubuntu.com/ports/releases/8.04.1/release/](http://cdimage.ubuntu.com/ports/releases/8.04.1/release/)

There is also a list of known issues: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

I hope this can help you.

---

### Post by felix_mc on 2008-07-22
Thanks! The alternate CD booted into installation successfully! However it took me a while to get the partitioning right, and I'm not even sure if I got it right now. I divided my 40 GB partition in three. A 2GB swap partition (RAM x 2, right?), a 1GB NewWorld Boot partition, and the rest 37GB an ext3 partition that mounts at root ('/').
The installation went well in the beginning, until it got to installing the yaboot boot loader. It said that it failed to install and that my partition might not be bootable, and that I should install it manually. I tried to reinstall it a few more times from the CD, but with the same results.
How do I go about installing it manually so I can boot into Ubuntu? None of the Ubuntu partitions mount in OS X, and only the swap partition is recognized it Disk Utility. The other 2 appear as 'free space' :(

---

### Post by komputes on 2008-07-22
That seems fine but I am not too familiar with NewWorld Boot or yaboot boot loader since I have never done this myself. I have found the following URL's

[http://yaboot.ozlabs.org/](http://yaboot.ozlabs.org/)
[http://developer.apple.com/documentation/Hardware/DeviceManagers/pci_srvcs/pci_cards_drivers/index2.html](http://developer.apple.com/documentation/Hardware/DeviceManagers/pci_srvcs/pci_cards_drivers/index2.html)

So OSX is not able to read your ext3 filesystems but Disk Utility is able to see swap space.
Is there an addition to OSX to read ext3?

This is what I found:
[http://forum.insanelymac.com/index.php?showtopic=34227](http://forum.insanelymac.com/index.php?showtopic=34227)

---

### Post by avtolle on 2008-07-22
You might want to take a look at the Apple Users Forum: [http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328)

I've two G4 Cubes, and had to first install from the alternate cd; then, I had to manually edit my /etc/X11/xorg.conf to get the GUI. Do you have a copy of any older xorg.conf file that you could make reference to for assistance?

---

### Post by felix_mc on 2008-07-23
Okay guys, so it turns out my alternate CD was scratched and therefore the install always failed when installing yaboot. I burned the iso to a new cd and the install went smoothly. However I ran into some video issues and the GUI wouldn't load. With the help of these forums I was able to find a xorg.conf  file that matched with my mac's hardware and I made the appropriate modifications.
Then I rebooted  and unlike previous times the graphics seemed to be working (the commands ran after the reboot command weren't overlapping, and the ubuntu 'logo' before reboot didn't look distorted like before, if that makes sense).
However now, I seemed to be stuck in Terminal mode. Unlike before the screen didn't just go black after the loading window, it went straight into terminal mode(as if I had pressed Control+Alt+F1). Control+Alt+F7, Control+D or the exit command only restarts the terminal mode (which asks for my username, password and then it's just a bash prompt).
How do I exit terminal mode and get Ubuntu to load the GUI?:confused:
Thanks for all the links and stuff so far. Really been helpful :)

---

### Post by komputes on 2008-07-23
Great news! :)

If you only get a terminal (white on black full screen) terminal, you can start the graphical interface by logging in and using one of the following commands:

$ gdm #This will bring you to the graphical login

or

$ startx #This will bring you to the default desktop manager (I think)

Let me know if these work. If so, the trick will be how to fix it so that it starts up in graphical mode on a regular basis.

---

### Post by felix_mc on 2008-07-24
okay, I tried both of them, and neither seemed to work..
When I did 'gdm', a warning came up about a gdm-daemon-confic.c file and an error on line 2033. Cannot run seteuid to 0.
With 'startx' the screen goes black as if something is about to come up, but then nothing happens. The screen just stays dark.. 
:(

---

### Post by komputes on 2008-07-24
hmmm. try the following:

sudo killall gdm
sudo gdm start

anything then?

---

