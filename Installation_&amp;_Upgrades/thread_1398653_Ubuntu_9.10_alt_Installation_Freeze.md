---
title: "Ubuntu 9.10 alt Installation Freeze"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by eroomydna on 2010-02-04
Hi all! 

I'm looking for some assurance from some of you more experienced Ubuntu pros. 

I have just rebuilt my laptop with 9.10 using the Alternate ISO as I wanted to be the master of an encrypted LVM. The installation got to 'setting up users and passwords' and the progress bar hit 26% and that's where it stayed. 1st time around I left the machine for 2 hours (just to be sure) and then rebooted. It booted in to a fresh 9.10 installation. 

My question is has my install completed okay? Can I check this fact somehow? 
Has anyone else experienced this issue?

Other info: I did check the media and it was fine. I even reburnt my ISO a couple of times and at the lowest speed. I downloaded the ISO again and burnt it. This all said the problem could be my hardware. 

I've also been able to switch into another terminal and run commands so my system hasn't completely frozen. 

As always, thanks for reading.

---

### Post by kevinpet on 2010-02-05
I'm seeing the same issue with NBR i386 on an eee 1000he.

Frozen at 26%, "setting users and passwords".

So I'll restart it and see if everything works.

---

### Post by caironet16 on 2010-02-12
Hello,

I too can confirm this bug, 9.10 32bit install dvd, setting up encrypted partitions using the alternate installer, when you reach the end of the install it reads "settings users and passwords" or something to that effect and both of my installations froze at 25% regardless of leaving it.

I pressed ctrl-alt-del and both systems did a reboot as if nothing happened.

But I too am worried that the drives encryption either isn't working or installed at all or if anything has gone wrong.

Things seem to work fine on my Dell Inspiron 6400 notebook but my Generic PC has a problem with the network manager, it has internet but when you right click the icon and choose "connection information" it says "Error displaying connection information: No valid active connections found!" despite me writing this very post from that system.

Haven't had these problems with Ubuntu before which makes me think its because of the installation problem.

---

### Post by empimp on 2010-02-13
Just reporting another user whose run into the "setting users and passwords" freeze.  

I was installing the Server v9.10 for i386 on an old box from work.  Like eroomydna and caironet16 I chose the encrypted LVM .  After having overcome several other challenges, the install made it to the "setting users and passwords" 25% and hung there for while.  A basic search brought me to this page.  Based on caironet16's comment I'm reinstalling now with the non-encrypted LVM (better safe than sorry).  Wish me luck! ;)

---

### Post by linux4me on 2010-02-13
Have a look at this [bug report]("https://bugs.launchpad.net/ubuntu/lucid/+source/ubiquity/+bug/432422/comments/15"). The title of the bug report isn't applicable, but some of the discussion, starting at #15, may be. It sounds like you can still use encrypted LVM, but select "no" when it asks if you want to encrypt your home directory, but if it's really not hung--although 2 hours seems like it might have been in the OP's case--waiting might be a better option. I have installed x64 on a few machines using the alternate CD with encrypted LVM and haven't experienced this, but those machines have been pretty robust hardware-wise and the delay might have been much less as a result.

---

