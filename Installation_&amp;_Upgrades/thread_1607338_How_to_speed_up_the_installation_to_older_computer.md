---
title: "How to speed up the installation to older computers?"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by Naoyuki Tai on 2010-10-27
Hello, 
My name is Tai, and I do a volunteer work for World Computer Exchange, or WCE, a non profit org.
WCE get a lot of old-ish (gettins less P3s, and more P4s now) computers, install Ubuntu and ship them to schools, libraries, etc. to the developing countries.
When I say Ubuntu, I often intall Xubuntu since the machines are slow, but if it meets the Ubuntu requirement in terms of memory and disk, we often install Ubuntu Ubuntu.

And, installing Ubuntu in general takes time. Most people don't notice "it's slow", but if you install it to a 10GB IDE ATA4 disks, it often takes a few hours. I can do it to a handful of machines but there are so many machines to deal with.

I modified the installer to do unattended installation so it is less of hassle now but I'd like to know what I can do to speed up the installation.
If it's faster, we'd be able to go though a lot more machines.

Also, it would be great if it's an easy process without network. I personally use a network (pxe boot and unattended installation), but there are many volunteers and it's logistically far easier if it can be installed without it.
I give out a modified CD to those volunteers and they just put it in and watch the progress of installation. Since machines often have issues with hardware, it's not a simple process even if it's unattended installer.
I'm wondering if there are people doing something similar and solving this kind of problem.

Thanks.

-- Tai

---

### Post by sikander3786 on 2010-10-27
First of all, incase you didn't go across that already, Lubuntu is far lighter than Xubuntu. Or probably a minimal install of Ubuntu + LXDE.

You can consider cloning disks using any cloning software like clonezilla. It will most probably save some time.

Regarding hardware, I only find graphics card a bit of trouble for installation. As far as you don't install proprietary drivers, it should be trouble free with older hardware.

I don't really yet ever come across any other way of speeding up the installer with such an old-ish hardware. Cloning is the easiest option in my opinion.

---

### Post by Naoyuki Tai on 2010-10-28
Thank you for the reply. I'll take a look at Lubuntu. 

> **sikander3786 said:**
> You can consider cloning disks using any cloning software like clonezilla. It will most probably save some time.


One thing I'm not sure about Clonezilla is that, I don't know how can I partition the disk the way Ubuntu likes it. Since the disk size is not uniform, it probably requires some kind of human interaction to partition the disk. The process is error prone.
I don't know how I can partition the disk as partman does. If I can customize the clonezilla to do what partman does to every disk, this would be a good option.

The second problem with Clonezilla is, the image does not fit on a CD, so I can do it easily but not for other volunteers who can only use CD as installation media. I guess I can boot from one Clonezilla, and use another CD, or possibly USB stick for image file. So, this problem may be solvable, but not ideal.

The third problem is that Clonezilla is interactive. I have to learn how to customize it to be as close to unattended as possible. One of problems is that, volunteers may not be well trained.

So, these things are preventing me from using Clonezilla, and using the unattended Ubuntu installation CDs.

-- Tai

---

### Post by wandalalakers on 2010-10-29
Remastersys
[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

I have created customized Xubuntu CDs using Remastersys but if you add extra stuff, the image might have to be put on a DVD.

---

