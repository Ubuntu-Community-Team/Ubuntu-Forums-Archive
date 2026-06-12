---
title: "How to copy root partition?"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by IamAcoconut on 2007-01-12
I am planning to setup an encrypted root partition, but first have to copy root filesystem to another partition (yeah, I really have to). Can it be done just like that - cp from say hda2 to hda4, then format hda2 and the system's ready to boot, or there's something more complex to it?

Thanks in advance :)

---

### Post by jd65pl on 2007-01-12
It may be best to re-install to achieve this ability as you may have issues with references to hardware locations. 

You may wish to investigate some sort of drive backup software to  backup and restore your root partition.

---

### Post by IamAcoconut on 2007-01-12
The backup is on it's way (Partimage), yet I still wonder what happens if I just copy the root partition to another. Will it be able to boot at all, or there's something that should be done to allow that?

---

### Post by jd65pl on 2007-01-12
It definately won't boot if you move your root partition to another drive location as grub will have an incorrect target i.e. will be looking for a drive which is not there. You should be able to repair grub with a live cd and indeed I have done this. However other programs which you have installed to the original disk may encounter difficulties. It is a bad Idea to install to one hd to copy to another and then expect the system to run the same as the original install,

---

### Post by IamAcoconut on 2007-01-12
I see. So partimage wouldn't help much?
Anyway, I'm planning for Ubuntu to reside on the same partition it's on now, but I have to clear and encrypt it first. So I'll probably make a backup with partimage, and restore everyhtng after partition is encrypted.
Well, as soon as I get the answer to my question here: [http://www.ubuntuforums.org/showthread.php?t=199824&page=8](http://www.ubuntuforums.org/showthread.php?t=199824&page=8)
I mean, that they have the boot partition there, and I don't. 
- Or it makes no difference whether boot is a separate partition or written to '/'?

---

