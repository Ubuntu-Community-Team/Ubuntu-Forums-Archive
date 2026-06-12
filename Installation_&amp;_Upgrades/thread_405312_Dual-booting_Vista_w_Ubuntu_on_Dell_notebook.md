---
title: "Dual-booting Vista w/ Ubuntu on Dell notebook"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by Gadren on 2007-04-09
I'll be getting a new laptop for college sometime this week -- a Dell Inspiron.  It will come with Vista already installed (and I believe that it comes with a recovery disk -- can someone who's ordered from Dell confirm this?).  I'm wanting to set it up so I am dual-booting Vista with Ubuntu.

Can someone give me a link to a guide that will walk me through the steps for this?

Also, I'm wanting to set it up so I have my 160GB hard drive split into three parts: one to hold Vista and all my games, one for Ubuntu, and one for data so I can easily access everything from both OSes.  How would I do this?

One more thing...I'm wanting to heavily customize both OSes, to strip off the Dell crapware from the Vista installation, and to rebuild my Ubuntu installation just the way I like it.  I understand that ubuntu-core is a meta-package that really links everything together.  If I installed Ubuntu and then wanted to remove gnome (without installing Kubuntu instead), would the link with ubuntu-core be a problem?  I've heard that it's needed to make a smooth upgrade.  What can I do there?

Also, I assume that if I store all my data and music and stiff like that in the third, common partition, I could do a fresh reinstall of Ubuntu on the second partition without impacting that other partition, right?

---

### Post by Threnners on 2007-04-09
I just got my new E1505 today and the "recovery disk" is actually a seperate partition, assigned to D:  That's about all I can  help you with.

---

### Post by Gadren on 2007-04-09
So, is it only a partition, with no actual disc?

---

### Post by BDwinsAlt on 2007-04-09
Yes, it is a partition.  I have a Dell Inspirion 1501.

I had to use this guide to get mine to work.  If ubuntu doesn't recognize your hard drive add the pci=nomsi option when the install screen comes up and asks you to install or boot.  hit F6 and type that.

Good luck.

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

---

### Post by ceciliaFX on 2007-04-09
I don't know anything about Vista - and never want to use it - but when I got my Dell Latitude about 4 years ago i also wanted to turn that into a multiboot system. i informed the Dell Dude of this and made suire i got the Windows2000 system CD(s).

I and a friend installed Red Hat and then Installed Windows. I made several Fat partitians so linux could read AND write to them. I don't put any data on the linux areas. 

Dell (at least when i did this) makes special system CD's that can only be used on DELL machines. In other words, I can't install the Windows2000 on any other laptop other than my Dell.

I hope to be able to install a newer linux where the Red Hat lives. maybe Ubuntu can be this upgrqade for me.

---

### Post by confused57 on 2007-04-09
You might want to read this thread:
[http://ubuntuforums.org/showthread.php?t=404200](http://ubuntuforums.org/showthread.php?t=404200)

See the 2nd link in my signature for installing with the Desktop Live cd.

---

### Post by st33med on 2007-04-19
Your new Dell might come with a Dell WLAN 1390 or an ATI, which Ubuntu 7.04 has a problem with. Visit these threads for more on it.
This one is for both:
[http://ubuntuforums.org/showthread.php?t=399913&highlight=E1505]("http://ubuntuforums.org/showthread.php?t=399913&highlight=E1505")

This one is for the wireless only:
[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

I'm not sure which wireless option will work for you. Try the bottom one first.

---

