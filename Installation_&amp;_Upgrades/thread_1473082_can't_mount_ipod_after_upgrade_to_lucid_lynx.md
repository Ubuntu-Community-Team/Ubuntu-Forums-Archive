---
title: "can't mount ipod after upgrade to lucid lynx"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by blindape on 2010-05-04
Hi, a few days ago I upgraded from karmic koala to lucid lynx and pretty much everthing has been working fince since then.  However this morning When my wife went to eject her ipod shuffle after charging it, she couldn't find it listed under mounted drives.  I have had a look round and also tried my ipod but ubuntu wont read that either.  If I run Disk Utility from the System menu, I can see that the ipod is there but it wont mount.  All my other usb devices have mounted and worked perfectly since the upgrade it has only been the ipods that wont work.

I have scoured the forum but haven't seen anything that directly relates to my problem.

Any help would be much appreciated.

Regards,

John Curwood

---

### Post by andricas on 2010-05-05
I had the same problem when upgrading from 9.10 to 10.04 beta. Problem persisted after a clean install of the final version. I can mount other USB devices but not an iPod, though the iPod shows up when I run dmesg:

> 
[ 8961.661361] usb 2-2: new high speed USB device using ehci_hcd and address 4
[ 8961.812796] usb 2-2: configuration #1 chosen from 2 choices
[ 8961.859551] Initializing USB Mass Storage driver...
[ 8961.860761] scsi4 : SCSI emulation for USB Mass Storage devices
[ 8961.860848] usbcore: registered new interface driver usb-storage
[ 8961.860850] USB Mass Storage support registered.
[ 8961.861577] usb-storage: device found at 4
[ 8961.861579] usb-storage: waiting for device to settle before scanning
[ 8966.861712] usb-storage: device scan complete
[ 8966.862260] scsi 4:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 4
[ 8966.863204] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 8966.867912] sd 4:0:0:0: [sdb] 2037504 512-byte logical blocks: (1.04 GB/994 MiB)
[ 8966.871116] sd 4:0:0:0: [sdb] Write Protect is off
[ 8966.871124] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 8966.871131] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 8966.874202] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 8966.874212]  sdb: sdb1
[ 8966.880298] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 8966.880301] sd 4:0:0:0: [sdb] Attached SCSI removable disk


Also, when I was running the beta upgrade whenever I restarted the system with the iPod connected it would mount. Now with the clean install that doesn't work anymore.

---

### Post by Michal77 on 2010-05-05
The same here :-/

---

### Post by MasterKush010 on 2010-05-05
Ipod mount issues here ... Disk utility picks up the ipod but gives no  option to mount.

very irritating.. dont want to use itunes software but have tried a lot  of open source software i.e Hipo Ipod manger, Banshee, Mpman.... no  mount.

all was ok before ubuntu v10

Have to use windows to load podcasts .... one day I will be able to  delete that partition!!!  

Please, can we have an update on ipod mount issues :wink:

Cheers, Kush

---

### Post by plindqvi on 2010-05-07
Hi,

Same problem for me. The Lucid upgrade broke the support for my iPod  (an old 1Gb Shuffle). With Karmic the iPod was automatically mounted and seen by Rhythmbox.

The Disk utility recognizes the iPod, but it is not mounted. Programs as HiPo and podsleuth says "No iPods were found in the HAL device tree".

Cheers,
Peter

---

### Post by blindape on 2010-05-07
Well since the only replies I've had for this thread are other people experiencing the same problem, maybe I should report this as a bug.

Any suggestions?

---

### Post by lashram on 2010-05-07
Wow I have an Iphone 3GS and when I did my upgrade to Lucid from Karmic Rythymbox automatically finds it when i connect it and it shows up in the side pane. I can even drag and drop my music and videos/movies to it and then it automatically syncs. Im not sure what i did different when upgraded or if that even matters but I upgraded using the update-manager -d option. I read on here that a lot of user favors clean installs though. I was amazed how it recognized it because Itunes would not install in Wine and I did not want to go back to using it anyways hence is why i switched to Ubuntu.:guitar:

---

### Post by Michal77 on 2010-05-08
> **blindape said:**
> Well since the only replies I've had for this thread are other people experiencing the same problem, maybe I should report this as a bug.

Any suggestions?

Rapport a bug. Seems old ipods lost support...
M.

---

### Post by blindape on 2010-05-10
All right, I'm going to file a bug for this.  Could everyone who replied with the same problem post again giving the details of their ipod?  For instance the ipod I can't get working are both old **512MB ipod shuffles**.

The more details we can get for the bug report the better.

Cheers,

John

---

### Post by andricas on 2010-05-10
Mine is a 1GB 1st generation iPod shuffle.

---

### Post by Michal77 on 2010-05-10
The same model here.
M.

---

### Post by kshome on 2010-05-12
I am having the same problem after upgrading to Lucid from Karmic. I have a 3rd generation ipod nano. I think this has to do with HAL removal in Lucid. I have found that keeping the ipod connected if you log out and then again login and then start banshee. The ipod becomes visible for syncing using banshee.

---

### Post by Michal77 on 2010-05-12
I found a way around. I did install Pysdm. It's a storage device manager. I can use it to mount Ipod. Later all operation are available like always. I use gtkpod. Downside is, that one need to use Pysdm to mount and unmount Ipod each time, but it's always something, before we can back to normal.
M.

---

### Post by m4n_in_bl4ck on 2010-05-12
> **kshome said:**
> I am having the same problem after upgrading to Lucid from Karmic. I have a 3rd generation ipod nano. I think this has to do with HAL removal in Lucid. I have found that keeping the ipod connected if you log out and then again login and then start banshee. The ipod becomes visible for syncing using banshee.

Try this:

[http://ubuntuforums.org/showpost.php?p=9277776&postcount=7](http://ubuntuforums.org/showpost.php?p=9277776&postcount=7)

Hope you get your iPod working with Banshee.

---

### Post by euux on 2010-05-13
Same here, can't mount an oldie 512 mb shuffle.

---

### Post by plindqvi on 2010-05-15
Mine is a first generation Ipod shuffle 1 GB.

---

### Post by blindape on 2010-05-16
Hi Everyone, I added the bug to Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578194](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578194)

I recommend that everyone affected go to this bug and add a comment saying that it also affects you and give as many details as possible including ipod model and version.

Cheers,

John

---

### Post by vogelkopp on 2010-05-20
hi guys,
found this bugreport 
[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971)
and removing the libgpod-common solved the problem for me too.
(ipod shuffle 1. gen 512mb) :)

---

### Post by andricas on 2010-05-23
Thank you for the tip! That worked for my 1st gen iPod 1GB.
I can even use banshee now to update my music library.

---

### Post by kshome on 2010-05-25
> **m4n_in_bl4ck said:**
> Try this:

[http://ubuntuforums.org/showpost.php?p=9277776&postcount=7](http://ubuntuforums.org/showpost.php?p=9277776&postcount=7)

Hope you get your iPod working with Banshee.

I tried this. it did not work for me. I also tried removing libgpod-common, but it still does not work. Nothing works for me right now.

---

### Post by euux on 2010-05-26
It worked for me!!! Many thanx! 
:guitar:

---

### Post by caseyboardman on 2010-05-27
Removing libgpod-common worked for me - mounts fine.

However, no matter what I do, any track updates (or deletions) are not saved on the iPod.  Looks like it may be a bug: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/496681](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/496681)

1st generation 1GB Shuffle.

---

### Post by alcarola on 2010-05-31
Hi! 

I have the same problem. Disabling the floppy in BIOS makes automount work once for every time i boot my computer. The BIOS trick was suggested in the thread: [http://ubuntuforums.org/showthread.php?t=1470705](http://ubuntuforums.org/showthread.php?t=1470705)

The iPod gets automounted once and only once per boot since i removed libgpod-common as suggested. 

Any clues why automount works only once?

Thanks,
Mikael

---

### Post by kshome on 2010-06-03
After a recent upgrade of podsleuth. My Ipod can now be synced with banshee.

---

### Post by kamaliitm on 2011-12-28
For me it's entirely strange.....

My iPod is not detected at all...not even by Disk Utility...what do I do? Please help

Thanks,
Kamal

---

