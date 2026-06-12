---
title: "Kernel Panic redux"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by Andrew1963 on 2006-11-20
I am trying to install kubuntu onto my laptop - a Packard Bell EasyNote with a 1.2 GHz processor and 512M RAM. It has a 50G disk, which is currently partitioned as follows:

hda1: hidden VFAT volume with Windoed Restore (8G)
hda2: NTFS with windows 2K Pro (16G)
hda5: Linux swap (0.5G)
hda6: SuSE Linux / (8G)
hda7: /home (14G)

My problem - with both Ubuntu and Kubuntu - is that when I reboot using the install CD it gets no further than the initial boot up when I select install.   Anyone got any solutions ?

---

### Post by louieb on 2006-11-20
You will just have to look up some of the boot up options for the kernel and try a few. For example I have one computer that freezes just after the kernel loads, my way of getting around that is to use the ide=nodma option. 
Another option I see mentioned alot is noacpic. 
I know this is kind of hit or miss but unless someone with your same hardware remembers what they did and responds.....
Sorry but can't remeber where I saw the list of options for Ubuntu. But I'm sure with a little searching you can find it.

---

