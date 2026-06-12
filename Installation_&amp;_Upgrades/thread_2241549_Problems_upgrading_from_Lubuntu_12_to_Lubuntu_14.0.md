---
title: "Problems upgrading from Lubuntu 12 to Lubuntu 14.04"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by CAstudent on 2014-08-26
I have been running Lubuntu 12.04 and decided to upgrade to 14.04 using the upgrade button on the system update program. The upgrade seemed to go well until it came time for the reboot. After my computer rebooted, Lubuntu showed a message that the hard drive had errors and it ran a scan of the hard drive (I suspect my HD is going out, it is an old computer). Well after Lubuntu completed the HD scan it rebooted my computer again, but did not finish the installation. Instead I was brought to a black screen with a mouse cursor. I could move the mouse and right-clicking brought up a small menu with shortcuts, programs and some options for Openbox, and a few other things. The only things that would open were the terminal and a menu to change some setting, no other programs would open. 

After some research I followed the directions given here: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) When I got to the installation type window I had to choose "something else" because the screen said I had no other operating systems installed (which I thought was odd because I also have WIndows XP on a partition of my HD). I followed the directions on the reinstallation page and finished the installation, but my computer will still only boot up to the black screen. I guess this is Openbox, which I am not familiar with and do not want to use. 

I did back up my home folder before upgrading but I would rather not go through the process of doing a new installation and needing to reconfigure all my setting and reinstall some of my favorite programs. How do I fix or finish my upgrade so I have the regular Lubuntu desktop environment?

ETA: I can go to "switch user" but after I enter my password the computer will briefly show the new Lubuntu background, then switch back to Openbox.

---

### Post by CAstudent on 2014-08-27
Since reinstalling from a DVD I have checked the MD5SUM of the .iso and used the "check disc for errors" function on the DVD; both checks were good. I have also used the DVDs memory test to check my RAM, with no errors. I can run Lubuntu from the liveDVD, so it doesn't seem to be a hardware issue. 

I have also used the instructions here ([https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)) to check my harddrive for errors using the smartmontools, while running from the liveDVD. The hard drive test completed with no errors. When I entered the badblocks command I was given a message that it could not run while the drive was mounted so I stopped there as I wasn't sure of any possible bad consequences to unmounting my harddrive; this was also while running from the liveDVD. 

I will continue to update things I try as I continue my research, but any help would also be appreciated.

---

### Post by claracc on 2014-08-28
I don't think you have a faulty hard drive.

The problem is lubuntu 12.04 reached its end of life support a long time ago, repositories have been removed from server, for this reason the upgrading haven't worked and you boot to a black screen.

What I would do is to backup the home folder and make a fresh install of lubuntu 14.04.

---

### Post by CAstudent on 2014-08-29
Ok, I did not know that Lubuntu had a different support time frame. Thanks. I did a fresh install and have my main computer back up and running. I did learn quite a bit while trying to fix my upgrade, so it wasn't a complete waste of my time.

---

