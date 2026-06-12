---
title: "Transferring to a new computer"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by K.Morgan on 2008-06-04
Hi, I will be purchasing a new laptop soon and as i have spent ages customizing my version of Ubuntu hardy on my desktop i was wondeing how easy it would be to transfer to a laptop.  If i was to do a clone of my desktop hard drive onto my new laptop hard drive and then started the laptop would Ubuntu sort out all the Hardware changes automatically for the new machine or is this asking too much.

I remember trying the same thing with Windows XP a while back and caused all sorts of problems, was hoping that Ubuntu would work better.

---

### Post by avtolle on 2008-06-04
> **K.Morgan said:**
> Hi, I will be purchasing a new laptop soon and as i have spent ages customizing my version of Ubuntu hardy on my desktop i was wondeing how easy it would be to transfer to a laptop.  If i was to do a clone of my desktop hard drive onto my new laptop hard drive and then started the laptop would Ubuntu sort out all the Hardware changes automatically for the new machine or is this asking too much.

I remember trying the same thing with Windows XP a while back and caused all sorts of problems, was hoping that Ubuntu would work better.
AFAIK, the clone will NOT sort out the hardware changes, differences, etc. automatically, and you may well find yourself in worse shape and spending more time trying to figure it all out than you would spend with a clean install. It is my considered opinion that you don't try this, but do a clean install and configuring it as necessary.

---

### Post by wpshooter on 2008-06-04
> **avtolle said:**
> AFAIK, the clone will NOT sort out the hardware changes, differences, etc. automatically, and you may well find yourself in worse shape and spending more time trying to figure it all out than you would spend with a clean install. It is my considered opinion that you don't try this, but do a clean install and configuring it as necessary.

I agree.

---

### Post by VMC on 2008-06-04
Just to put a different slant on this topic. I did exactly what your purposing. I was using another Linux Distro. I had a laptop with a defective CD-ROM drive, the USB was non bootable. Here's what I did. And actually you have several options.

First I removed the notebook hard drive, put in a 2.5" to 3.5" converter. Then installed Linux from my desktop. I then reinstalled the 2.5" back into my laptop.
After bootable up it complained and sent me straight to root prompt. I then ran the video, and sound configuration programs and presto, it worked. I haven't tried this with ubuntu.

The second option I used was, Grub4Dos. I installed that and then installed my Linux ISO, and did the loop-back method. It's described at the Slackware site. Inside Slackware ISO is a file called Install that takes off from there.

I probably wouldn't have even tried these methods if I had a decent CD-ROM drive, but I'm glad it happened. It gave me another option, albeit convoluted.

---

### Post by tamoneya on 2008-06-04
here is how I would do it:
1) use remastersys to make a custom ISO with all of my programs
2)install with remastersys
3) copy over ~/ because this is where all the configuration settings for you programs are stored.

---

### Post by K.Morgan on 2008-06-06
Oh well I guess it was a long shot.

I thought maybe Ubuntu would just recognize the new hardware and adjust it's settings accordingly, maybe eventually something like this will be possible, but for now will have to start again.

Cheers

---

### Post by edgeeffect on 2009-06-24
> **avtolle said:**
> AFAIK, the clone will NOT sort out the hardware changes, differences, etc. automatically, and you may well find yourself in worse shape and spending more time trying to figure it all out than you would spend with a clean install. It is my considered opinion that you don't try this, but do a clean install and configuring it as necessary.


I really don't understand why this is the case. I've cloned systems before using SuSE, Slackware and Debian. What is it about Ubuntu that makes it (to be honest) so rubbish in this particular area.

---

