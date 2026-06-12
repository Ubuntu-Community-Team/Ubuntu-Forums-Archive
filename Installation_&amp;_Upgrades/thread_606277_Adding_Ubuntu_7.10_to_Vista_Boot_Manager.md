---
title: "Adding Ubuntu 7.10 to Vista Boot Manager"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by nope2dope on 2007-11-07
Hi there, I had a dual-boot setup with XP installed first, then made some free space for Ubuntu for ext3 and swap. I had it setup with Grub for a bit, then installed Vista. I have it dual-booting XP + Vista right now. I have Linux still on the system, just need to conquer being able to add it to Vista Boot Manager. Also, is there a way to add it to Vista, and instead of it defaulting to the Grub, it would just automatically boot Linux? I hate waiting, so if it can just boot it right up, that's awesome. I think that's just as easy as removing the timeout option, not sure how to do it, but give me any info you have on all this, thanks.

---

### Post by logos34 on 2007-11-07
> **nope2dope said:**
> I have Linux still on the system, just need to conquer being able to add it to Vista Boot Manager. Also, is there a way to add it to Vista, and instead of it defaulting to the Grub, it would just automatically boot Linux? I hate waiting, so if it can just boot it right up, that's awesome. I think that's just as easy as removing the timeout option, not sure how to do it, but give me any info you have on all this, thanks.

yep.  Just change timeout to '0'.  (if you ever want to pause the boot for the menu, hit ESC as soon as you see 'Grub loading...').  

To add linux entry to vista:

[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

Or just go back to Grub bootloader on the mbr (and add vista entry to menu.lst):

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

