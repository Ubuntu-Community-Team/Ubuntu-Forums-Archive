---
title: "rsync to copy ubuntu to another partition possible?"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by frafu on 2007-02-27
Hello, 

I have edgy on hda1
I had another copy of edgy on hda2.

Then I made "update-manager -d" on ubuntu on hda2 to upgrade it to feisty. Unfortunately, feisty does not even start: it gives some interrupt error on hde and hdg which are sata drives. 

Can I simply make with rsync a copy of edgy from hda1 to hda2 and afterwards adjust fstab and menu.lst on hda2 to have again a working system on hda2? 

Is it possible? 
If so, are there other files I have to adjust manually? 

Thanks in advance for any help? 

Francesco

---

### Post by dinomite on 2007-02-27
That ought to work, though you might have problems with the bootloader, if it's configuration was changed.  Sounds like you have a non-working system currently, so you might as well give it a try.

---

### Post by frafu on 2007-02-28
I tried it today and the system on hda2 started up. However, it had among others a few issues with Synaptic and the Update Manager. 

I think it is because I did not provide the right options to rsync and the result is a mix between the former system (feity) and the copied system (edgy). 

I will give it another try. 

If somebody could tell me what options to use with rsync, that would probably be helpful to me. 

Have a nice day. 

Francesco

---

