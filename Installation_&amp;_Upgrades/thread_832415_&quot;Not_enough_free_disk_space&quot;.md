---
title: "&quot;Not enough free disk space&quot;"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by jacob1207 on 2008-06-17
I am trying to upgrade to Ubuntu 8.04 (don't ask me why) and when it gets to the second step, "setting new software channels", I get the following error message:

> 
Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 1217M free space on disk '/'. Please free at least an additional 256M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I have entered "sudo apt-get clean" in the command prompt and have emptied my trash, all to no avail.  

Some questions: (1) What the hell is this '/' thing of which this message speaks? (2) How do I free up additional disk space on it? and (3) How would a person of normal intelligence who hasn't devoted his or her life to learning the salvific ways of free software ever figure this out on his or her own?  

Or am I missing the whole point?  Maybe I'm not supposed to be able to figure it out on my own.  Maybe the point is I'm supposed to be humbled at how awesome people who write this sort of program are for knowing what to do and they enjoy seeing me have to admit I don't know what the '/' thing is or how to free up space on it?

Help me out here.  I do want to upgrade: it's free.  But I guess it's still true that you get what you pay for: software that only experts can use without help.

---

### Post by avtolle on 2008-06-17
/ refers to your root partition. How large is it, if you know. If you don't, at the terminal```
df -h
``` will give you information as to the size of the HDD, and the size of the various partitions among other things.

---

### Post by jacob1207 on 2008-06-17
> **avtolle said:**
> / refers to your root partition. How large is it, if you know. If you don't, at the terminal```
df -h
``` will give you information as to the size of the HDD, and the size of the various partitions among other things.

Okay.  But how do I make it  more bigger?  Or eliminate needless stuff from it so that I can upgrade?

---

### Post by avtolle on 2008-06-17
How are you upgrading? Through the upgrade manager or by a clean install from a CD?

---

### Post by wpshooter on 2008-06-17
> **avtolle said:**
> How are you upgrading? Through the upgrade manager or by a clean install from a CD?

My "guess" is that they are doing it thru upgrade manager.

Should they not just install "gparted" if it is not already installed and use it to manipulate the size of the partitions ?

Would their running a fsck possibly do them any good ?

---

### Post by avtolle on 2008-06-17
I'm guessing that they are doing it through the update manager as well. The reason I asked the question is that to resize the partitions, using gparted from a live cd will be needed. I think likely the best way to proceed would be to d/l a copy of gparted from sourceforge, burn it to cd, and then resize the /partition, but if installation was from a Live CD of 8.04, we could skip that step and just use the 8.04 Live CD for this purpose. Running fsck might also do some good, too, but I think resizing the / partition is the way to go right now.

---

### Post by jacob1207 on 2008-06-17
> **avtolle said:**
> I'm guessing that they are doing it through the update manager as well. The reason I asked the question is that to resize the partitions, using gparted from a live cd will be needed. I think likely the best way to proceed would be to d/l a copy of gparted from sourceforge, burn it to cd, and then resize the /partition, but if installation was from a Live CD of 8.04, we could skip that step and just use the 8.04 Live CD for this purpose. Running fsck might also do some good, too, but I think resizing the / partition is the way to go right now.

I was using the update manager, but I do have a CD.  So... what buttons do I push to make this work?

---

### Post by avtolle on 2008-06-17
> **jacob1207 said:**
> I was using the update manager, but I do have a CD.  So... what buttons do I push to make this work?
I'm already late to meet the wife, so this is going to be quick, and summary in nature. Boot the Live CD; when it comes up, then ALT+F2; in the box enter gksudo gparted. You should then be in the partitioner. Navigate to the / partition, and select the resize option. Hopefully, there will be enough room "at the end" to enlarge the partition. Backup any important files first, though, just to be safe. HTH, and good luck.

---

