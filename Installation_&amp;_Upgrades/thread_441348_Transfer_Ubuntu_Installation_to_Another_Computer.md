---
title: "Transfer Ubuntu Installation to Another Computer"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by zarmando on 2007-05-12
Here's a question for the technicians here:

**Is it possible to transfer a Ubuntu installation from one computer to another computer ?**
I have a running feisty, and I'd like to transfer my whole system to another new computer -- I have to send back the other one (faultya MoBo).

**How does one do that ?**

Would  "imaging" be the best option ? (That's what I would do if I was using Windows)
How do I circumvent driver issues ?
Will it even boot ???

Thanks A LOT for any suggestions or advice.

Z.

---

### Post by aysiu on 2007-05-12
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup) will help you.

---

### Post by zarmando on 2007-05-12
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup) will help you.


Thanks a lot for the link, aysiu! That was quick.

The problem with, let's say, "image backup"  is that, according to the site, it allows :
"Using the same Ubuntu configuration on several of computers that have the **exact same hardware**."

The thing is that I might have to replicate the image on **a different computer** -- same cpu though.

Any ideas, comments?

Thanks again!


P.S. : I didn't realize it was YOUR site. Congratulations. An amazing achievement.

---

### Post by aysiu on 2007-05-12
It may be okay with different hardware, but you're always safer with the same hardware.

This thread may be encouraging to you:
[ Massive hardware change, Ubuntu doesn't skip a beat!!!](http://ubuntuforums.org/showthread.php?t=345084&highlight=beat+hardware)

---

### Post by zarmando on 2007-05-12
Wow. 

Yes, indeed... Thanks for the encouragement. :)
I guess I'll just take the plunge !

Thanks aysiu.

---

### Post by runesvend on 2007-10-06
I'm curious :). Did you succeed in migrating your Ubuntu installation to a computer with different hardware?

Cause I'm about to do the same. The new computer has a different motherboard, CPU (Intel instead of AMD), new type of RAM, video card and network card. I'll be reusing my current PCI SATA controller, sound card, keyboard, mouse and HDs + CD-ROM/RW drives.

---

### Post by cudaman73 on 2007-10-06
I don't think that it will accept the change from AMD to Intel very well (as there are separate modules built into the kernel for each platform.

I'm pretty sure that the specific modules for each processor architecture must be built in directly to the kernel (i.e. not a module), so, if i'm right, you'd have to recompile your kernel (or install a new one). Other than that though...

I could also be totally wrong. Try it, but have a livecd of some sort on hand and be ready to install another kernel :P

---

### Post by runesvend on 2007-10-06
Ok, thanks for your reply! I will try it in a few days when I get the new computer.

If a new installation *is* required, is it possible to get all my installed programs from the installation on my old computer transferred to the new installation?

---

### Post by jml75 on 2007-11-02
Switching AMD to Intel will not be a problem because they are both x86 processors.

The only problem that may occur is with X. You may have to install the proper drivers (ATI or NVIDIA) and then run dpkg-reconfigure xserver-xorg.

But that is it!

---

