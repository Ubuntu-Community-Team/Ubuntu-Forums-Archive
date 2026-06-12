---
title: "Install OK but error at reboot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by ChrisXC on 2010-05-01
Hi,

I was thinking of recycling that old PC : P IV, 1,5 GHz.
The installation went fine (and fast) (I chose to erase everything to install). System asked me to reboot.
And I get a long list of errors on a black screen.
The last one says :
2125.145599 end_request: I/O error, dev sr0, sector 501144

Is there something I could do ?
Or is there no hope...

Thank you.
Chris

---

### Post by mhgsys on 2010-05-01
Looks like a harddrive is failing...

I/O errors ./ read write errors.

But sometimes it's a little bugled somewhere and your lucky.
Try completely powering off the system for a moment, and try again.

edit' ps; Also.. try removing all attached devices like printer, external hd etc.

---

### Post by ChrisXC on 2010-05-01
Thank you.

I tried disk utilies from the CD. It said the disk is OK, but I tried formatting the disk : no go.

However, I could format the volume. So I tried intalling again, but same problem of long list on black screen after rebooting.

Since the system works fine from the CD, I'm afraid you're right and there is a problem on the disk (there is nothing attached to the computer : keyboard, mouse and screen, that's all). I'll try again later with another disk.

Thanks again.
Chris

---

### Post by ChrisXC on 2010-05-01
Well, actually, that's different.

I can start with the CD. After offering a choice a languages, the screen shows a few different options.

If I choose the option at the bottom (start from the first hard drive, or something like that, loose translation), the system loads just fine (asks for password).

It's like the system needs to bypass something difficult at the beginning, and then works fine.


Chris

---

### Post by mhgsys on 2010-05-01
Could be a master/slave setting

most likely ; meaning a jumper problem..

Is there a (cdrom) drive  attached to the same ide cable as your harddrive?
Is it on cable select perhaps?

(in that case ;one should be master and one should be slave: f.e (dvd) on master and (disk) on slave

Try detaching the (cdrom) drive.. if the system boots fine from hd it is most likely not a failing hard drive but a master slave setting gone wrong.

---

### Post by ChrisXC on 2010-05-01
Bingo !

The disk was on a different cable than the CD drive, but it was not at the last position on it's cable. 
I recently removed another hard drive, that was at the end of the cable (had been added after), and I didn't change the position of the remaining one.

Now everything works. 
Now, I'll just have to learn how to use the system !!!

Thank you so very much.
Chris

---

### Post by mhgsys on 2010-05-01
Great it's working out for you now, 

I hope you realize there just  was a master/slave (jumper) problem between the two disks.

You should be able to attach the second disk as well if you want to, just make sure the masterhd is on master and slavehd is on slave.

edit; please add a [solved] "tag" to your original posting/thread.

---

### Post by ChrisXC on 2010-05-01
Yes,

I understand the problem of the slave/master hard drive.
I wouldn't have guessed because the disk was running windows without problem.

I hope the solved tag will appear this time.

Thanks again.
Chris

---

### Post by mhgsys on 2010-05-01
> **ChrisXC said:**
> 
I hope the solved tag will appear this time

Thanks again.
Chris

Your absolutely welcome  ; 

Go to thread tools > mark this thread as solved

---

