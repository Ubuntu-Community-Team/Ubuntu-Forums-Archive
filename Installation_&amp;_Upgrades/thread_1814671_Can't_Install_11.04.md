---
title: "Can't Install 11.04"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by SavageFreedom on 2011-07-29
I am trying to do a clean install of 11.04 on my Lenovo z565 which has the Radeon HD 5470 graphics chip. I'm trying this from CD as well as from a thumb drive. I haven't gotten anywhere near the actual installation process, as the boot-up hangs, then finally continues until I get to a screen of rapidly scrolling, seizure inducing text that flashes by for a solid minute or two before reaching the initramfs prompt. At this point I am clueless as to where to go. I've seen posts referencing this issue after Ubuntu has been installed. It seems Radeon might be the culprit, but I don't know how to fix this without even being able to boot into the Ubuntu installer. I can neither boot into the Live CD nor run the installer. I apologize if this issue has been covered already, I just couldn't find a thread that described all of my symptoms. I will provide any info needed, if possible.

---

### Post by 2F4U on 2011-07-30
I would first attempt to add "nomodeset" (without the quotes) to the kernel boot line. It helped me several times when an ATI card makes problems. It disables kernel mode setting, i. e. the early start of the kernel ATI driver.

---

### Post by YesWeCan on 2011-07-30
F6 on the menu

---

### Post by SavageFreedom on 2011-07-30
Doh, I forgot all about this. Will try it now, thanks so much guys.

---

### Post by SavageFreedom on 2011-07-30
When I press F6, nothing happens. It appears the only thing I can do is press ENTER or TAB to edit, and I tried adding nomodeset in place of splash, and the installer hangs on stdin: error 0 (which up until now it has never done.) I may try re-burning the .iso, but I have a feeling that isn't the issue.

---

### Post by sinisterair on 2011-07-30
> **SavageFreedom said:**
> I am trying to do a clean install of 11.04 on my Lenovo z565 which has the Radeon HD 5470 graphics chip. I'm trying this from CD as well as from a thumb drive. I haven't gotten anywhere near the actual installation process, as the boot-up hangs, then finally continues until I get to a screen of rapidly scrolling, seizure inducing text that flashes by for a solid minute or two before reaching the initramfs prompt. At this point I am clueless as to where to go. I've seen posts referencing this issue after Ubuntu has been installed. It seems Radeon might be the culprit, but I don't know how to fix this without even being able to boot into the Ubuntu installer. I can neither boot into the Live CD nor run the installer. I apologize if this issue has been covered already, I just couldn't find a thread that described all of my symptoms. I will provide any info needed, if possible.

I have a similar problem. I'm using my laptop an msi cr410 equiped with radeon hd4270. Mine have 1gb ddr3 ram. I'm not sure if the ram is the culprit.
U can say I'm a newbie.

---

### Post by SavageFreedom on 2011-07-30
Alright, I re-burned and used the CD. The USB installer wasn't working. The live CD gave me no issues at all. I'll mark this as solved I supposed, and make a new post for yet another issue I'm having.

---

