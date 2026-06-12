---
title: "Can't install"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by S@nctus on 2011-05-21
I've been trying to install 11.04 on my 2009 Macbook Pro, but I can't complete the installation because Ubuntu doesn't recognize my wireless connection.  Anyone had success with this?

---

### Post by sanderj on 2011-05-21
> **S@nctus said:**
> I've been trying to install 11.04 on my 2009 Macbook Pro, but I can't complete the installation because Ubuntu doesn't recognize my wireless connection.  Anyone had success with this?

I don't understand: Ubuntu can't complete the install? Of do you mean Ubuntu can complete the install, but your wifi is not working?

---

### Post by mörgæs on 2011-05-21
Did you have wired internet access while installing?

---

### Post by S@nctus on 2011-05-21
I don't have a wired connection, only wireless.  So when I get to the screen that says Try or Install, and I click Try (which is what I wanted to do in the first place) Ubuntu loads with no trouble, but I can't connect to wifi.  It's like Ubuntu can't see any wifi connections or something.  So then I tried the Install option, planning to install it along with Mac OS X but not to replace it, so I can dual boot.  Well, it gets to checklist and we get to the part where you have to be connected to the Internet, and of course since I can't get on wifi under Ubuntu, it won't go any further.

---

### Post by mörgæs on 2011-05-21
It far better to have wired internet access while installing. When that works, we can focus on the wirefree.

Isn't there some place close to you where you can get wired access for a few hours?

---

### Post by S@nctus on 2011-05-21
I don't have access to any wired connections.    The place where my cable modem is located is up high and coming out of the wall at an odd level.  I'd have to stand on a box and tilt my laptop weirdly on a narrow shelf just to position it for a wired connection -- and there's no way I could keep that going on for even half an hour, much less a few hours.  

Does it really take that long to get things up and running?

---

### Post by meloade on 2011-05-21
> **S@nctus said:**
> I don't have access to any wired connections.    The place where my cable modem is located is up high and coming out of the wall at an odd level.  I'd have to stand on a box and tilt my laptop weirdly on a narrow shelf just to position it for a wired connection -- and there's no way I could keep that going on for even half an hour, much less a few hours.  

Does it really take that long to get things up and running?

Why not just get a long Ethernet cable??????

---

### Post by S@nctus on 2011-05-21
I can get a long cable, but I live 30 miles from the nearest place that sells anything like that.  Seems like a lot of trouble to have to go to.
Why doesn't Ubuntu just know how to detect wifi networks like other OSes?

---

### Post by sanderj on 2011-05-22
> **S@nctus said:**
> I don't have a wired connection, only wireless.  So when I get to the screen that says Try or Install, and I click Try (which is what I wanted to do in the first place) Ubuntu loads with no trouble, but I can't connect to wifi.  It's like Ubuntu can't see any wifi connections or something.  So then I tried the Install option, planning to install it along with Mac OS X but not to replace it, so I can dual boot.  Well, it gets to checklist and we get to the part where you have to be connected to the Internet, and of course since I can't get on wifi under Ubuntu, it won't go any further.

I've never heard you need to have an Internet connection to be able to install Ubuntu from a CD. It's handy, but not needed. So I don't understand your problem. Maybe you should post a screenshot/picture of the message

Anyway: have you considered running Ubuntu in a virtual machine on Mac OSX on your Mac? It's probably easier for you; no network problems, no difficult dual-boot stuff. VirtualBox for Mac is a nice tool to run a VM.

---

### Post by mörgæs on 2011-05-22
> **S@nctus said:**
> 
Why doesn't Ubuntu just know how to detect wifi networks like other OSes?

Because not all hardware vendors are eager to support open source and provide details of their gear, which is needed for writing an open source driver.

Don't get me wrong. I am not saying that a wired connection is needed in all cases, it is just an easy step to prevent a lot of trouble. If a bug fix has been released, which helps getting the wirefree to work, we need the wired connection to download it, for example.

Which network card do you have?

---

### Post by S@nctus on 2011-05-22
I like the idea of running it in a virtual machine -- thanks!  I think I'll play around with that later today.  

My network card is Airport Extreme w/ Broadcom BCM43xx 1.0 (5.10.131.36.9) firmware

---

### Post by mörgæs on 2011-05-22
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

