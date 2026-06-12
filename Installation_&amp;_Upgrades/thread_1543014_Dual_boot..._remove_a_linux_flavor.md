---
title: "Dual boot... remove a linux flavor?"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by search66 on 2010-07-31
I'm currently dual booting Ubuntu and Mint... I want to remove Mint, and use that space for Ubuntu... What is the best way to do this?

Ubuntu was installed first; and then I installed Mint (FYI)...

---

### Post by sydbat on 2010-07-31
> **search66 said:**
> I'm currently dual booting Ubuntu and Mint... I want to remove Mint, and use that space for Ubuntu... What is the best way to do this?

Ubuntu was installed first; and then I installed Mint (FYI)...I'd boot a LiveCD and go into gparted and delete/format the unwanted partition, then resize the existing Ubuntu one. I'd also backup before doing this.

Oh, and afterwards, I would remove the Mint entires from grub.

---

### Post by search66 on 2010-07-31
> **sydbat said:**
> I'd boot a LiveCD and go into gparted and delete/format the unwanted partition, then resize the existing Ubuntu one. I'd also backup before doing this.

Oh, and afterwards, I would remove the Mint entires from grub.

Right on; I'll give it a shot.

---

### Post by LoREZ on 2010-07-31
If you are using Karmic or newer, GRUB 2 will probe the drives and remove the Mint entries for you, if I'm not mistaken.  Even if it's not automatic, you can manually probe for OS after startup. Just run this code at a terminal after you remove the Mint partition and are back inside an Ubuntu session:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

This probes the drive and saves what it finds, removing irrelevant entries at the same time, if memory serves.

---

### Post by search66 on 2010-07-31
OK... Im stuck a bit... I'm using a Live CD and I just nuked the other drive... I formatted it... 

/dev/sda1 is my Ubuntu which I wanna keep, and /dev/sda5 is my swap.

How can I get the other space to sda1?  I have sda2 and 'unallocated' I want to merge over.

The only options I have is: Manage Flags or Information.

(See screenshot)

---

### Post by search66 on 2010-07-31
Oops... I figured it out... The swap file was getting in the way... I nuked that and then recreated.  Thanks :)

---

