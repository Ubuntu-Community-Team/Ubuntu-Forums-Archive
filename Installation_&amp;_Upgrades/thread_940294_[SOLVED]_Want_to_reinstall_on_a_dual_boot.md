---
title: "[SOLVED] Want to reinstall on a dual boot"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by Morty007 on 2008-10-06
I have vista and ubuntu on my computer. For reasons I won't go into, I want to reinstall ubuntu. So...do I fire up gparted and delete the partition that has ubuntu on it and then reinstall that way? Or do I just install over what's there now? I want to keep vista on there for now.

---

### Post by Partyboi2 on 2008-10-06
Just install ubuntu again and when you get to the partitioning part choose manual and tick the option to format your / partition.

---

### Post by Morty007 on 2008-10-06
Ok. And this won't harm vista right? It will re-install grub I'm assuming?

---

### Post by Partyboi2 on 2008-10-06
correct, it should reinstall grub and it wont touch your vista partition unless you tick the wrong box to format.

---

### Post by Morty007 on 2008-10-08
Thanks for the quick reply, everything went well. :)

---

### Post by korkony on 2008-10-08
Hi Guys,
Re-installing Ubuntu after formating the Ubuntu partation will remove the boot list. Will the new Ubuntu be able to detect the current working Operating System (Vista in our case), so it'll bring it in the new booting list?!
I remember that didn't work for me before and I had to fix the booting of Windows XP later.
Can anyone confirm please??

---

### Post by devilscemo on 2008-10-08
hello to everyone.. i have a similar but i think more complicated problem. A friend of mine suggested 2 me to install ArchLinux... after a while I got frustrated with it because i liked Ubuntu much better as it was much more user-friendly for a noob like me... now the problem is i think i have a grub with Archlinux... i also have XP on my computer... what i would like to do is put Ubuntu and its grub on my computer (i would like to avoid having an XP boot since i know it messes things up).. O btw i have only 1 Sata Hard Disk with 3 partitions : Linux, XP, Documents... can any1 help?? thankyou so much

---

### Post by Partyboi2 on 2008-10-08
> **devilscemo said:**
> hello to everyone.. i have a similar but i think more complicated problem. A friend of mine suggested 2 me to install ArchLinux... after a while I got frustrated with it because i liked Ubuntu much better as it was much more user-friendly for a noob like me... now the problem is i think i have a grub with Archlinux... i also have XP on my computer... what i would like to do is put Ubuntu and its grub on my computer (i would like to avoid having an XP boot since i know it messes things up).. O btw i have only 1 Sata Hard Disk with 3 partitions : Linux, XP, Documents... can any1 help?? thankyou so much
If you installed arch after ubuntu was installed on your system try restoring grub from a live cd. [[COLOR=Blue]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") will explain how to do it.

---

### Post by Partyboi2 on 2008-10-08
> **korkony said:**
> Hi Guys,
Re-installing Ubuntu after formating the Ubuntu partation will remove the boot list. Will the new Ubuntu be able to detect the current working Operating System (Vista in our case), so it'll bring it in the new booting list?!
I remember that didn't work for me before and I had to fix the booting of Windows XP later.
Can anyone confirm please??
It should do.

---

### Post by devilscemo on 2008-10-09
no it was a new computer where arch and windows were installed (i think windows first so then linux could use the grub on MBR)... how do i set the UBUNTu grub on MBR? can i do this from the liveCD? thank you for help

---

### Post by Partyboi2 on 2008-10-10
> **devilscemo said:**
> no it was a new computer where arch and windows were installed (i think windows first so then linux could use the grub on MBR)... how do i set the UBUNTu grub on MBR? can i do this from the liveCD? thank you for help
If you haven't installed ubuntu then install it and the ubuntu grub should take over,  if you have already installed ubuntu then try using the live cd as I mentioned in the previous post.

---

