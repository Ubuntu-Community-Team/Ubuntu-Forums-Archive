---
title: "Upgrade to Lucid with /home Partition"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by AvixK7 on 2010-05-13
Hi all, I just need some clarification on the best upgrade path for me. I currently have Karmic installed with a separate partition for /home. I want to do a clean install of lucid with the CD. 

What's the safest way to ensure my /home partition remains untouched? Should I install lucid overtop the karmic partition and then indicate a mount point for the other partition? or should I leave /home alone completely during installation and then just manually configure the mount point after install?

Thanks!

Edit: I had previously upgraded from jaunty to karmic via the update manager. This worked well but Karmic has felt very buggy overall so I feel a clean install might be best. although the audio is silent when the live cd boots :S

---

### Post by howefield on 2010-05-13
> **AvixK7 said:**
> Should I install lucid overtop the karmic partition and then indicate a mount point for the other partition?

Yes, mount your /home partition but do not mark it for formatting.

You'd then need to install the applications that you previously had, there are a few threads on how to make this an easier task by taking a listing of your current packages.

Irrespective, you should be backing up what you don't want to lose, whether you are going through an upgrading process or not, disks can die.

---

### Post by AvixK7 on 2010-05-13
> **howefield said:**
> 

Irrespective, you should be backing up what you don't want to lose, whether you are going through an upgrading process or not, disks can die.

Thanks! This brings me to another question. My home partition luckily still has lots of space, I'm using about 130Gb out of roughly 400Gb. So I have room to back up. 

Is it safe to temporarily resize the partition using Gparted to create a backup partition without loosing my data? Then once the upgrade is complete and my data secure, I can delete the backup partition and resize the /home partition once more?

Thanks again :)

Edit: I have a portable HD but it's already full, so I don't have the means to make an external backup

---

### Post by darkod on 2010-05-13
> **AvixK7 said:**
> 
What's the safest way to ensure my /home partition remains untouched? Should I install lucid overtop the karmic partition and then indicate a mount point for the other partition? or should I leave /home alone completely during installation and then just manually configure the mount point after install?


As already said, you have to use the Manual Partitioning option, and tell Lucid to install on the partition currently Karmic root. You need to also mount the existing /home (and MAKE SURE the format box is NOT ticked), because it needs to know you have separate /home partition.

If you leave /home alone I believe a Home folder will be created in Lucid /, and not sure if you can switch to the existing /home partition later.

The process is very easy, I just did a clean install and not upgrade from Karmic too. I have separate /home just for that reason, to allow me clean installs (upgrades often have issues) but to be able to keep /home. Just make sure you don't format /home and that's it.

---

### Post by darkod on 2010-05-13
> **AvixK7 said:**
> 

Is it safe to temporarily resize the partition using Gparted to create a backup partition without loosing my data? Then once the upgrade is complete and my data secure, I can delete the backup partition and resize the /home partition once more?



Personally I wouldn't resize back and forth like that. Any resize by any tool is potential danger for your data if things go wrong.

Having said that, if you can't backup on external, you don't have too many options. I guess you don't want to invest in a new external hdd otherwise that would be best solution overall.

---

### Post by howefield on 2010-05-13
> **AvixK7 said:**
> Edit: I have a portable HD but it's already full, so I don't have the means to make an external backup

Do you have another computer you could network to, and pass the data across ?

Most likely you'll be fine and everything will go smoothly, but important data without backup is simply an accident waiting to happen. 

Disk space is so cheap these days.

---

### Post by AvixK7 on 2010-05-13
I'm in student dept at the moment, so investing in a HD isn't an option that's available to me right now :). I don't think anything would go wrong to be honest, but I do want to be careful whenever possible. I might try using the update manager first, see how that goes; but I'd rather have a fresh install.

Thanks for the advice. The resizing doesn't make much sense when you put it that way. 

If I installed Lucid in the / partition and left the /home partition alone during install, what would I do to get /home to mount automatically once lucid boots up? I remember correctly, doesn't Fstab exists anymore.

---

### Post by darkod on 2010-05-13
Not sure you can add it later. If no /home mount point is specified at install, Lucid will create it as a folder inside /.
Yes, you can edit fstab easily, but I'm not sure if it will work, if the permissions will match.

Another cheap alternative for backup is saving part of the data on DVDs.

---

### Post by howefield on 2010-05-13
> **AvixK7 said:**
> I don't think anything would go wrong to be honest,

Quoted for posterity ;)

> I might try using the update manager first, see how that goes; but I'd rather have a fresh install.

You could download the live cd and boot to the desktop, just to make sure that 10.04 will play nice with your hardware.,

> If I installed Lucid in the / partition and left the /home partition alone during install, what would I do to get /home to mount automatically once lucid boots up? I remember correctly, doesn't Fstab exists anymore.

Fstab does exist, and there are a shed load of tutorials/threads on here for this...

---

### Post by AvixK7 on 2010-05-13
> **howefield said:**
> 
You could download the live cd and boot to the desktop, just to make sure that 10.04 will play nice with your hardware.,



Fstab does exist, and there are a shed load of tutorials/threads on here for this...

I've already downloaded it. I get a strange error about something crashing (I'm at work so I can't recall what it says) and then loads up the desktop like nothing's wrong, I don't hear the ubuntu startup though. and I need ndiswrapper for my wireless but that's normal for the card I have.

yeah I know there's a bunch of tutorials :) I find the search function for the forums really dodgy sometimes. type in more that two words and the search turns up nothing.

Either way, I think I got the insight I needed, thanks a lot. :)

Edit: I'll post the results of my upgrade once I get around to doing it

---

### Post by howefield on 2010-05-13
> **AvixK7 said:**
> I find the search function for the forums really dodgy sometimes. type in more that two words and the search turns up nothing.

I agree, I think using google is often better than the forums search function.

Just append site:ubuntuforums.org to your search terms.

Good Luck :)

---

### Post by AvixK7 on 2010-05-13
> **howefield said:**
> I agree, I think using google is often better than the forums search function.

Just append site:ubuntuforums.org to your search terms.

Good Luck :)


hmmm never knew about that, thanks!

---

### Post by AvixK7 on 2010-05-14
Completed the upgrade throught the update manager. So far, everything is working as it should. I'm quite impressed. :)

thoughts: the broadcast menu doesn't impress much, I don't use microblogging so it doesn't appeal much. Ubuntu One doesn't work, like in Karmic. Dropbox for the time being is much better. Otherwise, the actual distro works great.

---

