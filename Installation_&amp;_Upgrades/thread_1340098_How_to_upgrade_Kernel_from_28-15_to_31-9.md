---
title: "How to upgrade Kernel from 28-15 to 31-9"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by josephe on 2009-11-28
Hi all
I found that my upgrade to Karmic has left my old Kernel 28-15 installed, how do I get it upgraded to 31-9 (or later I presume)

Thanks

---

### Post by wojox on 2009-11-28
Try:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by josephe on 2009-11-28
Hi there,

I'll have a go and let you know :-)

---

### Post by josephe on 2009-11-28
Hi there

Thanks for that, I had to shut down, boot up my Ubuntu Studio (which was the last OS I installed and so controls the boot loader) and alter its Grub config file as well, but my sound apprears to be back, even Skype works.

After a lot of time wasting ALSA tweeking for nothing, I probably broke more than I fixed in the end,
But I know have sound back.

---

