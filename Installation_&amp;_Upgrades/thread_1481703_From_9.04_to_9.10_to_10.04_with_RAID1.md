---
title: "From 9.04 to 9.10 to 10.04 with RAID1"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by clauswk on 2010-05-12
Maybe my experiences with upgrading to 10.04 can help others:

As a side job at work, I manage our little network consisting of 25 PC/printers etc and one file server (ubuntu) with one 120G system drive and two 1.5T drives (/home), hardwired as  RAID mirror. The file server was started approx. two years ago first as a standard ubuntu 8.04 desktop with samba. It worked perfectly for one year, then I decided to add a couple of big drives in a mirror configuration. At the same time, I upgraded to 9.04.
I had a little trouble making the mirror to appear as one drive, but finally I succeeded after researching the forums. It ended up by mapping a device like this: "/dev/mapper/jmicron_JRAID".

A few weeks ago I decided to make my 9.04 ready to upgrade to 10.04, meaning I had to upgrade to 9.10 first. It just happened without one single problem!

*(Amazing, but as a hardcore, and well experienced Windows user you expect all kind of problems)*.

Last night I decided it was time to upgrade to 10.04 LTS, and I followed the recommended steps to do so: Start update manager and click on Upgrade to 10.04. Pretty simple, and it was. It only took a couple of hours.

*And then I rebooted!*

An error message flipped onto the screen , but I couldn't read it - it was too fast.
Later on in the process of booting, a new error message came up, and this time I had plenty of time to read it. It goes something like this: **Cannot mount /home. Press S to skip or M to manually mount.** Ups, went all my users data out in the drain?

I didn't know what to do, so I pressed S, and the normal login screen came up. I tried to log in as a user, but couldn't (since there was no /home!!) Hmmm.
Back to my XP work PC and start WebMin. I looked at the same time on the internet to see if I could find a similar problem, but not really.

I then went into "Disk and Network Filesystems" and it appears as /home was mounted, but not in use. I tried to manually mount it, but got the message "The device file '/dev/mapper/jmicron_JRAID' does not exist"!!
To make a long story longer, I clicked on the little button [...] right to the 'Other device" field in Edit Mount, and two choices came up:
1 mapper/jmicron_JRAID
2 mapper/jmicron_JRAID____________

I tried the one with the many _underscores_ and mounted that device, and it worked!! ??
I don't know why some clever programmer decided to change exactly  that module that deals with devices, so your device name has to have underscores in the end - or maybe it was the other way around: got rid of underscores :-)

But my question is: Why change something that works? You can change the internals of the module, but why the interface?

But, now I am again a happy user of an ubuntu server. 

PS: The reason I use the desktop edition of ubuntu as a server is simple: When I started I had basically no experience with Linux, so I figured out I could play around with the file server and gain some knowledge in the Linux world. And I did!
And as long you don't log in, it only uses less than 200Mb, so that's OK.

---

