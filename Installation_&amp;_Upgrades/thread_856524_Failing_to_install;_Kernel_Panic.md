---
title: "Failing to install; Kernel Panic"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by vpjayant on 2008-07-11
Windows user was hoping to start getting used to Linux. Had Vista installed, was very happy. Downloaded Ubuntu. Did all checks to make sure it was not corrupted. Burned to disk, checked again. Tried to install. Installation failed midway through at some disk thing... not really sure what happened... the error was very unhelpful.

Attached is a screenshot of the error. 

Fiddled around trying to get it working and eventually it just froze. Turned off the computer, turned it back on, and it tells me it can't find an Operating System. This was most upsetting. So basically I lost everything. My fault for not backing up, I guess.

Anyway, I'm now trying to install Ubuntu, though I'm fairly certain there's something wrong with the HD formatting as at one point it tried to tell me that the HD was 5.8GB in size (it's 160GB)

Now when I try to install I get: 

invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

I'm completely new to any form of linux, and this laptop is now useless until I can get Ubuntu working on it. Any help on how to get this to happen would be greatly appreciated.

---

### Post by Pumalite on 2008-07-11
Burn a new CD. Do md5sum on the iso, burn at 4x or less. Do not use CD-RW. Check for CD integrity before install.

---

### Post by vpjayant on 2008-07-11
> **Pumalite said:**
> Burn a new CD. Do md5sum on the iso, burn at 4x or less. Do not use CD-RW. Check for CD integrity before install.
I get this error even when I try to check the disk. I already burned at 4x, I'm using CD-R, this is the third CD I've burned (same error every time) and I've done md5sums on the iso, and it seems to be fine.

EDIT: Burning again at 3x, redid checks, all seems to be uncorrupted. Maybe this will work? Doubt it.

EDIT 2: It did nothing. Downloading gparted and going to format the HD. Maybe that'll help.

---

### Post by Pumalite on 2008-07-11
md5sum is one thing. Checking for CD intetrity is another.

---

### Post by vpjayant on 2008-07-11
> **Pumalite said:**
> md5sum is one thing. Checking for CD intetrity is another.

I can't because I get this same error when I try to...


**EDIT:** Just did disk check on another laptop and all is well. Even started installing on another laptop to test and it worked fine. Something wrong with this laptop specifically.

---

### Post by Pumalite on 2008-07-11
Check options and see if you can boot your CD in verbose node. Maybe your CD Drive is not being recognized. At least find out where you are getting stuck.

---

### Post by vpjayant on 2008-07-11
Basically I can get to the first screen with the various options, so the drive is being found. But if I go to Install, demo, or disk check, it gives that error.

---

### Post by Pumalite on 2008-07-11
Getting to the first screen does not mean your drive is recognized during installation. There must be a log somewhere that shows you what is happening.

---

### Post by vpjayant on 2008-07-11
Deleted all partitions (there was an error in the main one), should I create a new one?

---

### Post by Pumalite on 2008-07-11
If you are going to use only Ubuntu; format your drive ext3. Install Ubuntu and use 'Guided>Use Entire Disk'

---

### Post by vpjayant on 2008-07-11
> **Pumalite said:**
> If you are going to use only Ubuntu; format your drive ext3. Install Ubuntu and use 'Guided>Use Entire Disk'

Formatted it to ext3; still getting same errors. Can't get to installation.

invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

---

### Post by Pumalite on 2008-07-11
I suspect your burner and your drive. Get rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Instructions to use it are in a Handbook.

---

