---
title: "Issues with my install (attempts rather)"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by sirwilliam1988 on 2007-12-30
Let me start from the beginning.

I bought two WD Raptor 150 harddrives for setting up RAID 0. I setup the raid0 and installed windows vista. I went to the store and bought a 250 gb harddrive (which is sata as well) and I planned to format it into two partitions. One for Windows XP Professional and the other for Ubuntu Linux. When I attached all cables to the drive, I then installed Windows XP Professional via Alienware Respawn (which is nortan ghost). However, the Vista boot manager doesn't see this drive, so I went into Vista and downloaded EasyBCD and added the entry. Then I went to the Manage option by right clicking on my computer and went to storage and the computer didn't recognize the drive. Then at the bottom right I got a notification window saying that MediaShield needed to format the drive. The only options were Jbod and Striping. I don't get it! How do I setup a system that is Raid0 for 1 OS and then have an extra harddrive to put on two partitions for the 2 other os's? 

In my bios (EVGA 680i) I went to integrated peripherals and then under the drives for raid the sata 3 primary/secondary are now set to disabled. However when I go into Vista Mediashield tells me that the drive needs to be formmated. When I pressed f10 and got into the raid bios I set the second harddrive (where xp was) to bootable. When it starts I got a blue screen of death and it restarted. When I selected the Windows XP entry in the vista boot manager it said it could not find NTLDR. 

So I guess here is what I am asking: How do I triple boot when I have a Raid0 setup with Vista and I am introducing a new non raid sata harddrive? 


And lastly, I booted off the Ubuntu disc and the install screen came up (with the other options). When I pressed enter, it started loading then the screen started flickering a couple of times and then timed out. By screen flickering, I could see/move my cursor for a little bit but then it came out with an error message about my device not starting. It gave me the option to select my device, which I did and still did not work. I tossed the disc, downloaded from a different mirror, and the same thing happened. I think that maybe the sli is throwing it off? I thought sli was a software thing, something you had to enable, like you do in vista. Is having the 2 gpu's throwing off the kernal?

My machine:
Alienware ALX
EVGA 680i sli motherboard
X6800 cpu
2 x 8800 gt in sli
2 GB ocz sli 1066 ram
1000 watt power supply


Sorry If I am confusing, I would love to clear anything up. I just want my baby (ubuntu) back.


-Sir William

---

### Post by sirwilliam1988 on 2007-12-31
Maybe I will just give up on Ubuntu.

---

### Post by sirwilliam1988 on 2008-01-07
no help? No wonder people don't switch over to linux! this is a joke.

---

### Post by Sef on 2008-01-07
> And lastly, I booted off the Ubuntu disc and the install screen came up (with the other options). When I pressed enter, it started loading then the screen started flickering a couple of times and then timed out. By screen flickering, I could see/move my cursor for a little bit but then it came out with an error message about my device not starting. It gave me the option to select my device, which I did and still did not work. I tossed the disc, downloaded from a different mirror, and the same thing happened. I think that maybe the sli is throwing it off? I thought sli was a software thing, something you had to enable, like you do in vista. Is having the 2 gpu's throwing off the kernal?

1) Did you md5sum the download?  (Makes sure it is good.)

2) Did you burn the iso as an iso?  (Not as a data disk.)

3) Did you burn the iso at 4x or less? (Faster can corrupt the download.)

4) Did you go to Check Disk for Errors instead of start/install?

> no help? No wonder people don't switch over to linux! this is a joke.

Why should anyone help you if you feel that way?

> Maybe I will just give up on Ubuntu.

That is your choice and you are free to do it.  We are all volunteers here, and so threads may take a long time to be answered.  If more than a day goes by, just simply click post message and type bump.

---

