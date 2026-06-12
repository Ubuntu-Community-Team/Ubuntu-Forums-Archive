---
title: "My Little Project"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Error47 on 2007-03-27
My Windows just shut down for good. I copied all my files to my external HD, and now I am ready to delete that partition. Is it possible to delete my Windows (and any others), and then resize my Ubuntu partition to use my whole HD?

Then I was planning to install VMware so I can run XP within Ubuntu. I have no clue how to do any of this. How does VMware work anyway, is it going to make a new partition, does it use my existing windows partition, does it make a virtual partition?  Oh, and can I install more than one windows, like XP and Vista, either one at a time or both at a time.

What would happen if I was to install Windows XP now, with Ubuntu installed? Could I duel boot, or would it just overight everything?

Just to let everyone know, I am a complete linux newb. I would need thorough instructions...Thanks.

---

### Post by raja on 2007-03-27
> **Error47 said:**
> My Windows just shut down for good. I copied all my files to my external HD, and now I am ready to delete that partition. Is it possible to delete my Windows (and any others), and then resize my Ubuntu partition to use my whole HD?

You can delete the partition and use the space. The easiest way to do it to format it as ext3 and mount it in your existing linux set up. For example you can create a mount point as /media/vmachines and use the space to keep your virtual machines

> 
Then I was planning to install VMware so I can run XP within Ubuntu. I have no clue how to do any of this. How does VMware work anyway, is it going to make a new partition, does it use my existing windows partition, does it make a virtual partition?  Oh, and can I install more than one windows, like XP and Vista, either one at a time or both at a time.


You can install VMware server. This will allow you to run virtual machines simultaneously. Each virtual machine you create will appear like an ordinary folder on your hard drive - so it doesnt create a separate partition. Yes, you can run different windows distros, other linux distros, etc in VMware.


> 
What would happen if I was to install Windows XP now, with Ubuntu installed? Could I duel boot, or would it just overight everything?

If you reinstall XP, it will overwrite the MBR and make it impossible to boot into Ubuntu. But you can restore the MBR then by one of many methods. 

For any of the above, if you want more details, you will find them in different places in the forum. If there is something specific you want to do and are not able to find it, post it here again.

---

