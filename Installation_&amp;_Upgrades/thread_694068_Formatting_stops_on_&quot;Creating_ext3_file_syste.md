---
title: "Formatting stops on &quot;Creating ext3 file system for /&quot; on a new hard drive"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by trymbill on 2008-02-11
Hi all,

I've had an Ubuntu Server for about 1 year now, with 7.10.  A few days ago my system crashed with the errors "Input/Output error" with everything that it tried to do.  I tried some stuff I found on the forums and also asked what I could do and got a few answers but nothing worked.  So I decided to try and setup Ubuntu 7.10 from skratch, but that didn't work.  The installation seemed to stop at 33% in the "Partitions formatting" with the message "Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0) (sda)..."

I thought it could be the hard drive, because it's really old, so I bought a new one today and installed it.  It's working fine, the BIOS finds it and the 2 other hard drives I've got installed but for some reason, Ubuntu 7.10 still stops at 33% in the "Partitions formatting" ...

I also tried 6.10 and 7.04 but they just do the same.  I don't get it!

Does any one know what's going on with my computer? :- /

---

### Post by Pumalite on 2008-02-11
Post your specs. If you can boot a Live CD (I doubt it) then post:
sudo fdisk -lu

---

### Post by trymbill on 2008-02-11
The computer is fine.  I've been running Ubuntu Server from 6.10 on this exact machine for a year now so there is nothing wrong with the specs.  The server started acting weird and started showing errors like "This is a read-only system" so I had to restart the machine, run fsck and then it was OK but in the 4th or 5th time it just stopped working completely.  So I thought it was the old hard drive, bought a new one, and it's still the same.

I can only run a "Live CD" with a desktop version of Ubuntu right?  I'm going to try that tomorrow.

I'm also going to try and disconnect all the other hard drives from the computer and see if the partitioning works any better.

If any one else can help me, please do so :)

---

### Post by trymbill on 2008-02-12
This is a bump ...
... a lot of forums submitted in here :)

---

### Post by Partyboi2 on 2008-02-12
Have you tried to install with the [alternate]("http://releases.ubuntu.com/releases/7.10/") cd?

Edit: Nevermind I see that you are trying to install the server version

---

### Post by trymbill on 2008-02-14
I was trying out VMware and setting up Ubuntu Server on it and it worked O.K. with Ubuntu 6.06 Server but then I tried setting up Ubuntu 7.10 Server, with the same specs as I tried on Ubuntu 6.06, and it froze again at 33% in the "Partitions formatting" in the installation progress.

Strange..!!

---

### Post by Pumalite on 2008-02-14
What are your specs?

---

