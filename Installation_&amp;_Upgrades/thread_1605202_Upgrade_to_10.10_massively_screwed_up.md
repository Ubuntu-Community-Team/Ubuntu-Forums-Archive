---
title: "Upgrade to 10.10 massively screwed up"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by cnidus on 2010-10-25
A power failure interrupted my upgrade from 10.04 to 10.10. I don't know exactly where in the process it happened. The upgrade was running overnight. Now, the machine hangs in the midst of booting. I have access to GRUB and can select among two kernels and the two associated recovery modes, none of which are Maverick kernels.  Using recovery mode, I can see that the last error is:

mount: according to mtab, none is already mounted on /lib/init/rw
mountall: mount /lib/init/rm [123] terminated with status 1

The system does not drop to a maintenance shell as expected.  And here is the fun part, there is no CD drive and the system will not boot from a USB, so I can't even do a clean install. I have an ethernet card that works. What are my options? 

Is there a way to force it to drop to a maintenance shell? Failing that what can I do from an initramfs prompt correct/fix the upgrade?

---

### Post by anarchy404 on 2010-10-25
You could try a network install

---

### Post by cnidus on 2010-10-25
I kinda of figured it would be a netboot kind of thing....

I was hoping for a little detail...

How do I get the network card up and running so that I can download/communicate with the outside world?

---

### Post by anarchy404 on 2010-10-27
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot) 

This should contain all of the information that you need. If not, just google the answers. If you have an ethernet port on your comp or a non-wireless network card plus a spare computer then this should all be easy.

Best of luck.

---

### Post by arcticice on 2010-11-11
Hi

I'm new to the forum but I've been an Ubuntu user for quite some time now. Instead of creating a new thread I thought I'd just borrow this thread since the title clearly explains my problem. I was upgrading my 10.04 to 10.10 last night, while it was installing I had to go somewhere urgently so I had to pack up my laptop, thinking it would suspend operations and it can continue where it left off at a later time. So when I got home, I setup my laptop hoping to see Ubuntu restore itself but to my surprise my laptop had shutdown. I tried to boot to Ubuntu but now I can't get past the loading screen and the usual Ubuntu logo had been replaced with "10.04" in text. It was stupid of me to interrupt the upgrade but is there a way for restart the upgrade process? Recover mode does not work either. I can still boot to grub though from the bootloader.

Any help would be greatly appreciated.

---

