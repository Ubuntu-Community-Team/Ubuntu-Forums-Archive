---
title: "Grub2 keeps ignoring default setting"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by dheianevans on 2012-08-15
I used to have an issue with Grub2 ignoring my default OS to boot but changed /etc/default/grub to:

			 				GRUB_DEFAULT="Windows 7 (loader) (on /dev/sdb1)" 			 		

as per this thread I was involved in: [http://ubuntuforums.org/showpost.php?p=11858921&postcount=873](http://ubuntuforums.org/showpost.php?p=11858921&postcount=873)

I had to reinstall Win7 a few months back and tonight used boot-repair to reinstall grub.

My Mythbuntu was the default. I made the above change and it was still Mythbuntu. did the  			 				GRUB_DEFAULT="Windows 7 (loader) (on /dev/sdb1)"  			 		and sudo update-grub and it was still mythbuntu. 

Wassup?

---

### Post by darkod on 2012-08-15
Do you have only one version of Mythbuntu and one version of windows?

Is the win7 recognized correctly after the reinstallation and restoring grub2? I assume it can boot OK?

Is the spelling of the menu entry exactly as the detected one?

Alternatively you can just use the number instead of the title. Don't forget it starts counting from 0. If the win7 entry is fifth for example, set it to 4 and it should be OK.

These days the entries don't move often even after kernel updates since the first time you do kernel update it creates an entry called Previous Versions and after that it puts all older kernels inside making all the other boot entries stay fixed without moving around.

---

### Post by YannBuntu on 2012-08-16
Hello
please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL.

---

