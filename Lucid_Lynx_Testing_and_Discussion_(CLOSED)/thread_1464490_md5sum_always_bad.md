---
title: "md5sum always bad"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kilz on 2010-04-28
I have been having a wierd problem, and I wonder if anyone else is. I cant copy or download iso's to burn. Because every time the md5sum is bad. What makes this so wierd is I can on karmic, the iso downloads fine. But if I stick it on a usb stick, check to make sure the md5sum is good (it is), then reboot and try to copy the iso to lucid its bad, every time. But the md5sum on the stick remains good.
I am using kubuntu lucid (64bit of course), everything up to date. Anyone else having this issue?

---

### Post by Grenage on 2010-04-28
Are Lucid and Karmic on the same machine?  Just ruling out bad RAM.

---

### Post by VMC on 2010-04-28
Kilz, what program are you using to download? Try downloading Ubuntu ISO from Kubuntu since it apparently works for its ISO.

---

### Post by Kilz on 2010-04-28
Yes both karmic and lucid are on the same machine, and on the same drive. I dont think it matters, but karmic is ubuntu and lucid kubuntu.
The iso file downloaded doesn't matter. I take care of a number of machines running Linux for others. I have tried different iso's from different sources. All are bad when a md5sum is done.
Neither does the application, a download through the browser and a torrent both were bad. I dont understand how a torrent could be because it has a hash.
One other strange thing I forgot to mention, when copying a good iso from a usb drive the md5 sum will be different each time. Bad but different.

---

### Post by Grenage on 2010-04-28
That's really odd, I wonder what is modifying the files.

---

### Post by null_pointer_us on 2010-04-28
How are you checking the md5sums?

Are you running Lucid native or in a VM?

I've experienced plenty of disk read failures (and silent corruption) in buggy VM releases. VirtualBox < 3.1.4 + guest smp were especially bad this way.

---

### Post by teh603 on 2010-04-28
> **Grenage said:**
> That's really odd, I wonder what is modifying the files.That makes two of us. I know of someone who was downloading the files thru a torrent client, and got an md5sum that was waaaaay off.

---

### Post by kansasnoob on 2010-04-28
Try using either zsync or rsync with these images:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Note the filter, and you may have to rename the existing image!

---

### Post by shaggy999 on 2010-04-28
My vote is on bad ram despite both OSs being on the same machine. I spent all of last weekend trying to get lucid installed but it broke down at a bunch of different places. This was despite the fact that I have run feisty through karmic with no problems. I even re-installed karmic and everything was fine. Finally I pulled a match set of RAM out and lucid installed fine. I then tested those sticks of RAM and they indeed ran into errors under memtest86. The problem was that for some reason lucid touched a bit of RAM that none of the other versions had.

In short, test your ram.

---

### Post by beow on 2010-04-28
> **teh603 said:**
> That makes two of us. I know of someone who was downloading the files thru a torrent client, and got an md5sum that was waaaaay off.

Happened to me when I downloaded Karmic via torrent half a year ago. Worked fine with http.

---

### Post by Kilz on 2010-04-28
Well it had something to do with the install itself. What I am not sure. I wiped the install and reinstalled, problem went away. My bet is a bad upgrade, corrupted file, or package. 
This install was from the first beta, and I normally wipe and reinstall on release, but the rc will have to do this time.

---

