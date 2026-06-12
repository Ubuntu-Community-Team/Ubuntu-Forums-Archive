---
title: "Boot-Grub Problems, among other things"
date: 2016-06-19
forum: Installation &amp; Upgrades
---

### Post by Victor_Gilbert on 2016-06-19
Help Can't re-install Grub. Can't install Adobe Flash Player. System keeps crashing
[http://paste.ubuntu.com/17575882/]("http://paste.ubuntu.com/17575882/")
Victor

---

### Post by deadflowr on 2016-06-19
*Thread moved to **Installation & Upgrades**.*
and also fixed the title:
(the paste link was the title, so changed the title to something more understandable and added the link to the thread.)

---

### Post by grahammechanical on 2016-06-20
> boot-repair is executed in live-session (Boot-Repair-Disk 32bit 29nov2014, trusty, Ubuntu, i686)

Are you running a 32 bit version of Boot Repair on a machine with a 64 bit install of Ubuntu? Why do you want to re-install Grub. If you want to load XP, then it is not there

> 1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS. 

Can you load Ubuntu? Re-installing Grub will not fix problems with Ubuntu crashing. 

> grub-pc purge cancelled 
Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again.

Have you done that? Is Ubuntu shut down? I cannot identify the problem you want help with. 

Regards

---

### Post by Victor_Gilbert on 2016-06-20
[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") 	 

 						Thanks Using 32 bit Boot Disk Repair Disk on 32 bit machine.

grub-pc purge cancelled 
Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again
Where do I go from here in Terminal when there is nothing to close?

 Adobe Flash Player freezes when checking grub.

Victor

---

### Post by Victor_Gilbert on 2016-06-20
[ Thanks]("http://ubuntuforums.org/member.php?u=1276577")   [**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1276577")

Will try to be more accurate in what I do from now on. Not easy at 78 and a Ubuntu simpleton.

Victor

---

### Post by oldfred on 2016-06-20
Boot-Repairs output shows issues with sources.

Post this. 
cat /etc/apt/sources.list.d

Please use code tags. You can easily add code tags with Forum's advanced editor. Highlight text & click on # icon.

---

### Post by Victor_Gilbert on 2016-06-22
Dropped dual boot. Gone for a new installation of Ubuntu 16.04.

Vic-sat

---

