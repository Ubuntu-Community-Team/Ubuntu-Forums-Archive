---
title: "How well does Jaunty support the Aspire one?"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-02-21
Anyone running Jaunty on an Aspire One, are you having any problems, does it work out of the box?

---

### Post by Sockerdrickan on 2009-02-21
I'm also interested in this

---

### Post by sonicb00m on 2009-02-21
Not yet, the wirless still isn't working and I didn't bother trying anything else after that. 

Tne new PCLinuxOS beta supports the unit out of the box....

---

### Post by Nullack on 2009-02-21
Network manager is closing in on RC so if would be so good as to debug it or report a bug that would help....Or is the problem a driver one?

---

### Post by nyarnon on 2009-02-21
I run it on an asus eeepc 1000h and I'm impressed with the stability of what is actually still alpha ware. Of course there are occasional updates that tend to give problems but again it is alpha. nice thing though about netbooks is that you are able to run for instants a stable intrepid on a usb stick. I always have one for the time Jaunty gives me hurt.

---

### Post by sonicb00m on 2009-02-21
> **Nullack said:**
> Network manager is closing in on RC so if would be so good as to debug it or report a bug that would help....Or is the problem a driver one?

Just unsupported by the kernel I think...no driver available.

---

### Post by Sockerdrickan on 2009-02-21
You can compile the madwifi driver if not

---

### Post by Lucretius on 2009-02-21
running it on an aspire one here with 1.5gb of ram

runs great...  everything works minus the wireless with network-manager

you need to install WICD for it to work.

I can not get the camera to work with canorama but it works fine with cheese.

apart from that everything seems great

---

### Post by son on 2009-02-21
You only need to 'sudo rmmod acer_wmi' and wifi comes on instantly. Add 'blacklist acer_wmi' and you have the problem fixed permanently. I cannot provide you the reported Launchpad bug, since the server seems to be unreachable here.

The annoying thing that left is that you risk losing all data on your SD card if you leave it inserted during suspension.

---

### Post by son on 2009-02-21
and another thing: it is confirmed that Jaunty is delivering a combined Intel graphic driver/X.org binaries that contain serious performance regression, due to ongoing refactoring of memory management bits. This affects machines having Intel card, not only the AspireOne. Not a real penalty in my case however, but you are warned :-)

---

### Post by Bossieman on 2009-02-22
Im on Jaunty and I use a special kernel that is optimized for AspireOne. You kan find the kernel here: [http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)
This little maschine boots faster than my ordinary computer with that kernel and everything works ootb.

---

### Post by Sockerdrickan on 2009-02-22
By the way:

**Can you record via the microphone?**

---

### Post by sonicb00m on 2009-02-23
> **Bossieman said:**
> Im on Jaunty and I use a special kernel that is optimized for AspireOne. You kan find the kernel here: [http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)
This little maschine boots faster than my ordinary computer with that kernel and everything works ootb.

Ah that's cool!

---

### Post by scaine on 2009-02-23
How quickly does an AspireOne boot up with the custom kernel?  I don't own an AspireOne, but I've built about 5 of them for friends using Intrepid and I find that on the 160Gb hard disk version, it boots in about 70 seconds (from "on" to "desktop finished loading"), which includes extras like OpenOffice quickstarter, Gnome-Do/Docky and such like.

Which is pretty good, but of course Jaunty is already much faster, so I'm wondering what impact the kernel has over that...

---

### Post by Limulus on 2009-02-23
> **son said:**
> You only need to 'sudo rmmod acer_wmi' and wifi comes on instantly. Add 'blacklist acer_wmi' and you have the problem fixed permanently. I cannot provide you the reported Launchpad bug, since the server seems to be unreachable here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319825](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319825)

See also [http://ubuntuforums.org/showthread.php?t=1042075](http://ubuntuforums.org/showthread.php?t=1042075)

---

### Post by son on 2009-02-24
> **Limulus said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319825](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319825)

See also [http://ubuntuforums.org/showthread.php?t=1042075](http://ubuntuforums.org/showthread.php?t=1042075)

That's it. Thanks

---

