---
title: "Help with boot repair"
date: 2022-12-10
forum: Installation &amp; Upgrades
---

### Post by aniruddha060 on 2022-12-10
[https://paste.ubuntu.com/p/2PDMPRJr4M/](https://paste.ubuntu.com/p/2PDMPRJr4M/)

I found a hard drive from one of my previous laptops and tried to see if it still worked by using it as my boot disk. While doing so, I switched to legacy boot before switching back to UEFI. The old hard drive would not even be detected so I switched back to my usual hard drive and tried to boot into Ubuntu but the partition with grub doesn't even show up in the boot optionns. As can be seen above, sda10 is the one with the ubuntu installation. However, I only see sda1, sda6, sda7, sda9 in the boot options. I already tried applying the recommended settings with boot repair. It hasn't solved my issue. However, I haven't made any changes to my windows installation that was recommended at the end of the pastebin. Is that the only way or is there something I can do to fix this issue?

Edit: 
 			 				[INDENT] 					Issue has been solved. I selected "Add boot option" and added the  first ubuntu efi file I could find and that solved my issue 				[/INDENT]

---

### Post by aniruddha060 on 2022-12-10
Issue has been solved. I selected "Add boot option" and added the first ubuntu efi file I could find and that solved my issue

---

### Post by oldfred on 2022-12-10
You can change to Solved.

Most UEFI, if you unplug a drive it loses or changes the boot entries for that drive.
And most UEFI do find the Windows entries again, but not any others.

You can use efibootmgr to add new UEFI entry. That is what Boot-Repair did probably by reinstalling grub.

---

