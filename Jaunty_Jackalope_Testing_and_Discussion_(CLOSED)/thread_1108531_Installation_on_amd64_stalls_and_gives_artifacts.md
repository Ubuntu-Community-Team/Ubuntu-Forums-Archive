---
title: "Installation on amd64 stalls and gives artifacts"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Maupertus on 2009-03-27
Hi everyone,

I downloaded the beta today, checked MD5, burned the image and booted the cd.

I have been googling my *ss of, but unlucky-me can't find the following problem and sollution.

When I boot from cd, everything is going on swimmingly, I choose a language and choose to install (or for that matter, test without changes). I then get a Ubuntu loading screen that fills up nicely, but at that point the screen turns black, I get 4 very distorted ubuntu logo's in the top of my screen and a mouse-pointer (that I can move with my mouse).

Nothing happens after that.

There is no damage to my system, but I really want to testdrive Jaunty and I hope this won't bid bad tidings for the RC.

Can anybody help, or has anybody seen anything like this? I'll try to take some legible pictures with my digital camera to post as explanation later on. 

Specs:
AMD64 3000+, 2Gig DDR RAM, 1x 160GB Samsung Spinpoint HD, 1x 250GB Western Digital HD (both S-ATA), ATI HD2600 512mb.

Thanks!

---

### Post by Nullack on 2009-03-27
AMD64 works fine for my sys

Boot with custom boot options, have a look at ubuntu debugging wiki on boot problems

---

### Post by loomsen on 2009-03-27
Again I'm tempted to suggest a netinstallation. Connect your PC through a cable [and see if it works... (Just enable the Ubuntu Desktop task when prompted)](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot)

---

### Post by Malcy on 2009-03-28
I'm having a similar issue. Towards the end of the amd64 install the screen just goes black and stalls.

---

### Post by Maupertus on 2009-03-28
> **loomsen said:**
> Again I'm tempted to suggest a netinstallation. Connect your PC through a cable [and see if it works... (Just enable the Ubuntu Desktop task when prompted)](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot)
You mean Unetbootin? I just looked in my BIOS, but it's a little bit to old (5 years) to allow USB-stick booting.

@Nullack: Which custom boot-options?

@Malcy: Hah! You're lucky, my system doesn't even get to install anything :)

Any known problems with ATI graphic cards during install? It's the only new component since I installed Intrepid.

---

### Post by Malcy on 2009-03-28
I have now got it installed. When it had been sitting around with the black screen, I tried a few button combos and ctrl-alt-del jogged it back into life. It asked me to remove the CD as it should but left the CD drawer locked! After that it booted up fully working. 

I have to say that I am impressed so far, a lot of apps, especially wine apps are so much faster that 32bit Intrepid. This is just a test install but I will be upgrading my main setup to 64bit when the final version is out.

---

### Post by loomsen on 2009-03-29
> **Maupertus said:**
> You mean Unetbootin? I just looked in my BIOS, but it's a little bit to old (5 years) to allow USB-stick booting.


Well, burn a disc then...

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/)

[Klick me, I'm the downloadlink](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/mini.iso)

---

