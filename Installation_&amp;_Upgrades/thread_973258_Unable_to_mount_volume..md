---
title: "Unable to mount volume."
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by everytimeref on 2008-11-06
After latest upgrades in intrepid I know get the following error when ever I insert my USB stick.

The error is nearly identical when I insert my Panasonic digital Camera ( I did get it working by upgrading libgphoto2, but after an official Ubuntu upgrade it died again) and  also when I try and mount my second HD (which has Windows on it) all these devices worked fine in Hardy

-----------------------
Cannot mount volume.

Unable to mount the volume 'MY STICK'.

IsCallerPrivileged() failed
------------------------
------------------------
Unable to mount MY STICK
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
-----------------------

'would be grateful for any help.

BTW I've checked permissions in Users and groups and the "access storage devices automatically box is ticked...."

---

### Post by jill.valentine on 2008-11-06
could you tell your ubuntu type n version? what kind of usb do you have? maybe we can get another clue.

---

### Post by everytimeref on 2008-11-06
Sorry, I've just upgraded to 8.10 from 8.04.1

It's a PNY 2gb USB stick, but I'm not sure if that's relavant as any thing I try to mount, including my Phone (sony k800i) my internal windows HD and my Panasonic Lumix TZ3 ALL come back with the same error.

It's all kit that worked fine in 8.04

---

### Post by everytimeref on 2008-11-07
Okay, Now I have no access to any drive other than my main HD,

I put a CD or DVD in a drive and it does not appear, no error message, I put in a USB key or camera and get the same thing.

What is happening???

---

### Post by everytimeref on 2008-11-07
When I go to Disk usage analyser I get the error message 


Could not detect any mount points

Mount from terminal gives me

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/myles/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=myles)

Any ideas??

---

### Post by dabl on 2008-11-07
Is your user a member of the fuse group?

---

### Post by everytimeref on 2008-11-07
No sorry,

I'm just a stuck inexperienced user who wants to sort my problems!

---

### Post by everytimeref on 2008-11-08
I used this thread:

[http://ubuntuforums.org/showthread.php?t=905509](http://ubuntuforums.org/showthread.php?t=905509)

to get this software: 
sudo apt-get install pysdm

That enables me to mount all my problem devices. But not my DVD devices, I can still play a video DVD in VLC so this seems to be an Auto mount problem.


Please can someone help me with this now as I've run out of ideas...

---

### Post by everytimeref on 2008-11-09
Well,

no-one was able to help me with this so in the end I ended up re installing intrepid. (after forcemounting a windows HD to back stuff up).

I'm only posting incase someone else has similar problems.

Will think long and hard before "upgrading" Ubuntu in April. That experience was awful.

Re-install by contrast is so much easier and hugley easier than any windows install....

---

### Post by Daveth on 2008-11-09
whilst little consolation to you, My Panasonic FZ30 has stopped being recognised on Hardy, despite working perfectly for ages beforehand. It does not even mount at the moment, though usb sticks do. I'm putting it down to some upgrade, but need to poke about a bit to see if this is so.

---

### Post by everytimeref on 2008-11-10
I had that problem when I first installed intrepid, I solved that like this :

[http://ubuntuforums.org/showthread.php?t=970391](http://ubuntuforums.org/showthread.php?t=970391)

---

