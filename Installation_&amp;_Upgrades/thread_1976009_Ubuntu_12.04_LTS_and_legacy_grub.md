---
title: "Ubuntu 12.04 LTS and legacy grub"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by ndhertubu on 2012-05-08
Is switching from GRUB2 to Legacy grub still possible in Ubuntu 12.04 LTS ?
 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) does mention a section 13.1 Reverting to GRUB Legacy,
the text looks unchanged compared to one year ago, 
but might it be outdated for Ubuntu 12.04 ? 
I hope not.
(the highest version mentionned in the text is 11.04)

---

### Post by grahammechanical on 2012-05-08
Are you using 12.04? Then you will be using Grub 2. Even if you started with 10.10 or earlier and legacy Grub was in place by upgrading to 11.04 and upwards Grub 2 would have replaced legacy Grub during the upgrades.

The old legacy Grub files will still be there but not used. On a new install everything will be Grub 2 or something like 1.99. You should see it on the Grub menu.

I know this because I learned how to modify the legacy Grub configuration files and then everything changed and I was back to being ignorant again.

I note these two comments in that wiki page

> Upgrading to GRUB 2 from GRUB (legacy) in Ubuntu 9.10 or earlier versions is relatively easy.

> Note however that the developers made a decision to not use an automatic update to GRUB 2 as the default on upgrade installs. Users who upgrade to Ubuntu 9.10 may continue to use GRUB if desired.

So, the purpose of the wiki page is to help users who want to convert 9.10 or earlier to Grub 2. Therefore it seems to me that the section on reverting back is those using 9.10 or earlier.

The instructions may work. It is your decision to try it. but I also note that the page was recently updated. But that does not mean that everything was tested on versions later than 10.04.

Note this

> This guide primarily details the use of Grub 1.98, the Grub release found in Ubuntu 10.04 LTS (Lucid Lynx).

Regards.

---

### Post by darkod on 2012-05-08
> **grahammechanical said:**
> Are you using 12.04? Then you will be using Grub 2. Even if you started with 10.10 or earlier and legacy Grub was in place by upgrading to 11.04 and upwards Grub 2 would have replaced legacy Grub during the upgrades.

The old legacy Grub files will still be there but not used. On a new install everything will be Grub 2 or something like 1.99. You should see it on the Grub menu.

I know this because I learned how to modify the legacy Grub configuration files and then everything changed and I was back to being ignorant again.

Regards.

However, after install you can enter your installation with chroot and completely remove grub2, and install grub1 (legacy). I think that is what the OP is talking about.

I haven't tried 12.04 with grub1, I have no need to do so. But if you want to boot it with grub1 you can try if it will work. If it doesn't, simply install grub2 back.

That's how you learn. Do in virtual box first if you prefer, no need to touch your main system just for a test.

---

### Post by flemur13013 on 2012-05-08
Grub is awful software, and grub2 is worse than grub1 (they weren't even smart enough to get the names and versions to match...), so I always uninstall grub2 (called v1.9 or some other inconsistent nonsense) and install grub "legacy" (or v.9 or some other inconsistent nonsense) and it works fine with 12.04, no problems at all.  All thru synaptic.

---

### Post by coyotito on 2012-12-06
> **flemur13013 said:**
> Grub is awful software, and grub2 is worse than grub1 (they weren't even smart enough to get the names and versions to match...), so I always uninstall grub2 (called v1.9 or some other inconsistent nonsense) and install grub "legacy" (or v.9 or some other inconsistent nonsense) and it works fine with 12.04, no problems at all.  All thru synaptic.

But you must add some other repo, right? There is no grub-legacy package in 12.04.

---

### Post by oldfred on 2012-12-06
Software names and versions have never matched. Grub legacy ended at version 0.97 and that is in the repository just as grub. 

Grub2 is the second rewrite of grub. 

In 12.04 it is at version 1.99 and should be updated to version 2 with the next point release. Ubuntu 12.10 uses grub2 version 2.00 now. Grub 2 is package grub-pc for BIOS and grub-efi for UEFI systems.

---

