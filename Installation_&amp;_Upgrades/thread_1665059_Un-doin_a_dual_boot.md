---
title: "Un-doin a dual boot"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Tayashlor on 2011-01-11
yes, again with the dual  boot questions. 

Due to school, I need to remove the ubuntu partition from my hard drive because I need space I allotted to ubuntu. 

I have an acer aspire one netbook.

I need to know how to remove Ubuntu and restore my hard drive without loosing my windows files (which are on a separate partition), 
I know i have to delete the ubuntu partition but what i am unclear of is what to do after that to restore windows as the primary boot. 

thanks

---

### Post by Quackers on 2011-01-11
If you have a Windows XP/Vista/7 (whichever version you are using) repair disc, or installation disc, you will need to repair the Windows bootloader with it.

---

### Post by ottosykora on 2011-01-11
Probably the biggest problem with the grub is, that it brings no uninstall means with it as other boot managers do.

Yes you can, delete all, but then you are stuck with the first part of the grub in your mbr and you will not be able to boot your windows any more.

What you need then , is repair the mbr so it points to windows again. This can be done with the installation disk of windows , repair console in XP for example or later windows have similar procedure, w7 you can create a boot disk for recovery purposes first. You just need the original boot disk and make sure it works before you go and wipe the ubuntu partition where probably the majority of your grub parts resides.

I never could understand, how can someone create a boot manager which is only installing itself, but has  no means of restoring the original state.
If ubuntu would come with proper, current technology (we have 2011 now, not 1990) boot manager, 90% of the help threads here will be gone.
But it is same as with the other operating systems from the 'competitor', just make my one the main, destroy the other one if possible seem to be the policy.

---

