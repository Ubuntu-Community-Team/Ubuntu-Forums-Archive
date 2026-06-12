---
title: "[SOLVED] Unable to moun drives..."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by DarkDancer on 2008-10-31
Ok, the main drive that I use will not mount. If I try, I get> The volume 'LDSilver' uses the EXT3 file system which is not supported by your system.   Followed later by > DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any help would be appreciated, and of course I will happily provide any info about the drive or whatever that you need....

---

### Post by DarkDancer on 2008-11-02
Bump....

---

### Post by DarkDancer on 2008-11-02
Ok, so I added this

> UUID=2a57aceb-dfb9-9520-983a-e26dbbdc4b95 /ldsilver       ext3    0       0

to /etc/fstab and now the drive has disappeared completely from nautilus.

---

### Post by DarkDancer on 2008-11-03
Anyone, anyone? Bueller, Bueller? Seriosuly, this is my main drive, and, oh yeah, the drive I am booting off of. A little of that famous ubuntuforums help would be nice....

---

### Post by DarkDancer on 2008-11-05
Ok guys, you're not being very helpful, but I'll keep trying to get you to try to help (even a "beats the junk out of me." would be better than being ignored).

Ok, so I followed the guide here:

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

This worked! Sort of.....

It puts the drive in a folder and Ubuntu seems to no longer consider it a drive. I really would prefer it be a drive. What do I do (an once again, a clueless utterance would at least be something).

---

### Post by zwygart on 2008-11-05
Sorry if you never had answer.

The page which you linked only shows how to mount basically on Linux. All linux mount partitions on directories (from where you access the drive).

I think this page will be helpfull for you, (it was for me)

[http://users.bigpond.net.au/hermanzone/p10.htm]("http://users.bigpond.net.au/hermanzone/p10.htm")

---

### Post by DarkDancer on 2008-11-05
Thanks Zwygart! That worked, though you wouldn't happen to know why Ubuntu thinks it's a photo cd would you???

---

