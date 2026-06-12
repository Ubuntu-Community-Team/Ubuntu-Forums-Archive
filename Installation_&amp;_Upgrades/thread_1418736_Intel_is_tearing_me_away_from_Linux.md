---
title: "Intel is tearing me away from Linux"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by ben44b on 2010-02-28
Good day, 

I've been using Ubuntu for a couple of years and for the most part, I like it. The most frustrating thing over the years has been my run-ins with Intel Graphics Chipset 845G (Brookdale). Since Karmic has come out, this chipset crashes Ubuntu and, months later, this has not been fixed. (See bug #456902). So I had to re-install Ubuntu 9.04. 

Thinking this was a Ubuntu problem, I went out and bought a Linux magazine with a Fedora 12 inside. This was after I had downloaded the same distro but couldn't get the install going because of the proverbial chipset. After re-installing 9.04, after I installed Fedora 12 twice, I am now back to a crappier display then the one I had when I decided to "upgrade" to Ubuntu Karmic in November. My patience with the poison brew of Intel and Linux is wearing really, really, really thin.

I cannot afford a new computer nor Windows 7.

My question is: Does Intel care about people who use Linux?

Thanks.

---

### Post by lykwydchykyn on 2010-03-01
> **ben44b said:**
> 

My question is: Does Intel care about people who use Linux?

Thanks.

They care about making drivers for it.  Whether they care about the people or not, I couldn't say.  But *most* intel hardware works quite well in Linux.

The 845 is a notorious exception.  I've reported a number of bugs against it for Lucid.  It no longer crashes, but compositing is not happening.

Your other option is to shell out ~$20 for an older NVidia card for a somewhat better experience.

---

### Post by Sef on 2010-03-01
>  My question is: Does Intel care about people who use Linux?

If you had read through the [thread]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902"), you will realize it is not Intel's fault.   (See post 36 in the thread.)

---

### Post by RJARRRPCGP on 2010-03-02
> **ben44b said:**
> Good day, 

I've been using Ubuntu for a couple of years and for the most part, I like it. The most frustrating thing over the years has been my run-ins with Intel Graphics Chipset 845G (Brookdale). Since Karmic has come out, this chipset crashes Ubuntu and, months later, this has not been fixed. (See bug #456902). So I had to re-install Ubuntu 9.04. 

Thinking this was a Ubuntu problem, I went out and bought a Linux magazine with a Fedora 12 inside. This was after I had downloaded the same distro but couldn't get the install going because of the proverbial chipset. After re-installing 9.04, after I installed Fedora 12 twice, I am now back to a crappier display then the one I had when I decided to "upgrade" to Ubuntu Karmic in November. My patience with the poison brew of Intel and Linux is wearing really, really, really thin.

I cannot afford a new computer nor Windows 7.

My question is: Does Intel care about people who use Linux?

Thanks.

845 is outdated. Sorry :(  

You should replace your motherboard with at least a socket 775 with GMA 3100 graphics. Then it should be fine. Sorry :(

Lucid Lynx alpha 3 is working like a charm with this config.

---

