---
title: "Other Boot Managers"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by damnwombat on 2005-09-08
I have recently installed Ubuntu for the first time; however, I have had prior linux experience.  My goal is to set up a boot record for XP Pro SP2, Ubuntu, and Solaris 10.  I have been able to set this up just fine using GRUB; however, I hate GRUB.  As do many of my friends.  I attempted to install LILO through Ubuntu's Synaptec Add/Remove Programs deal but when it finished installing and I went to set it up, it reported that it could not write to the MBR.  I assume GRUB's grip runs deeper than I imagine.  Anyhoo, to  point:

First of all, is there anyway that, like Solaris, it might be possible to actually create a small partition and expand the boot images to that drive so I might be able to merely make the drive active to boot, much like the way GRUB opens the images and then boots?  Would it also be possible instead to write GRUB to the first sector of the drive instead of in the MBR?  If either of these options is possible, that would be excellent as I could, in theory, start the computer however I like.  

If neither of those options are possible though, is there possibly another reason why LILO will not be written to the MBR?  Either way, I'd rather not look at text.  I am probably being vague on that but I'm on a different operating system right now, so I can't get to it to get details.

Thanks all,
damnwombat

---

