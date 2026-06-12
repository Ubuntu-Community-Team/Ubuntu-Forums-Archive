---
title: "Problem installing grub (after windows installation)"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by Blackie_Chan on 2005-06-24
Initially, I had ubuntu linux, then I installed windows xp (which changed my Master Boot Record).

Anyhow, now I'm trying to boot to linux again, and I can't.  Here's what I have done:

I used the live CD to boot.  At the **boot:**  prompt, I type 'rescue' and follow all the instructions.  Then I get to **sh#**. 

I read somewhere that I should try: **grub install /dev/sda11**    (where /dev/sda11 is where the linux partition is), but that just opened up the grub command line.  

At the grub command line the following: (in bold are the error messages that  I got)

grub> install /dev/sda11    **can not mount selected partition** 
grub> root (hd0,10)           **system type unknown partition type 0x82**
grub> kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/sda11 ro ** I got another error message but I don't remember it**

Anyhow, how could I boot to linux again?

---

### Post by frodon on 2005-06-24
there are several way to do that, i think this link will help you : [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

---

