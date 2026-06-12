---
title: "Installation failed, no RAID0 support?"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by crowz on 2012-09-17
Hi guys,

I was about to install Ubuntu 11.10 when I go a problem "...not possible to install the bootloader..." or something like that. It asked me another location to install grub, but I have just 2 disks in stripe mode or raid0.
Then tried to install 12.04, got problem with the swap partition :confused: but in the same point of installation, next the partitions' selection.
My computer is an AMD (FM1 socket) and it is the first time I try to  install Ubuntu on a stipe hard drive.
Now I remeber that I have already boot Ubuntu 10.04 and 11.10 from an USB Hard Drive and that I wasn't able to see my disk striped.

So I think Ubuntu doesn't support my motherboard raid option
What's your opinion?

---

### Post by darkod on 2012-09-17
For fakeraid (bios raid) installation you should use the alternate cd, not the standard live cd. It has better raid support and it doesn't fail when installing the bootloader.

If you did finish the install and only the bootloader is missing, you might be able to add it, but on the other hand it might be easier for you to do a new install again.

---

### Post by crowz on 2012-09-17
Thank you for your reply 
Alternate cd? mmmh ok I'll try it
I didn't finish installation cause I quit
I forgot to write in the same disk there's a Win7 hoping it's not a problem

---

### Post by darkod on 2012-09-18
No, it's not a problem if there is a win7. But you have to use the alternate cd for better raid support.

---

