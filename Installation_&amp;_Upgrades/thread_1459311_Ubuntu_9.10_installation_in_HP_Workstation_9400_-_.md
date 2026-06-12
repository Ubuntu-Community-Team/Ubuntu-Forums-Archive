---
title: "Ubuntu 9.10 installation in HP Workstation 9400 - Dual Boot"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by jsmanian on 2010-04-21
Dear All,

     I tried to install Ubuntu 9.10 in HP Workstation 9400. I partitioned C drive and created 25GB free space. I have one more HP auto recovery drive (D) also. Then I installed ubuntu in this 25GB free space. Installation was successful. It showed grub loader first time and I booted into ubuntu. It is working fine. But once I restart the system and boot into windows XP, the grub loader is not at all coming. It directly going into windows XP.

I tried to install one more time in OEM manufacturer mode also. The same problem came here also. When I restart the system after booting into win XP, it is showing the following error.

  [B] No such disk
   >Grub load error
   >Grub rescue[/B]

    Could anyone give suggestions how to make the system dual boot with win XP and ubuntu 9.10.

---

### Post by jsmanian on 2010-04-21
Could anyone give some suggestions? I am really struggling with this problem.

Thanks

with regards,
jsmanian

---

### Post by jsmanian on 2010-04-21
No one knows about this?:confused:

---

### Post by jsmanian on 2010-04-22
I tried to install grub loader from live cd and grub-update. Once I do this, I can see the grub loader and I can select the ubuntu or Win XP.

As long as I boot only into ubuntu, I can see the boot loader. But once I boot in to win XP, then I restarted my system, grub loader is not coming. And the following error is coming.

[B]grub loading
error: no such disk
grub rescue>[/B]


I am totally frustrated. I dont know what to do now.

---

### Post by andrewthomas on 2010-04-22
This should help you out
> **drs305 said:**
> [COLOR=MAROON][B][SIZE=4][CENTER][I]The Grub 2 Guide
(formerly Grub 2 Basics)[/I][/CENTER]
[/SIZE][/B][/COLOR]


**[COLOR=DarkRed]HP Machines  Fails to Load Grub after Using Windows -  Bug [/COLOR][URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941"]bug/441941/URL]**
After installing Grub 2 on a HP machine, the system boots normally until the  first time it's booted into Windows. On the next boot, the system hangs  at "Grub loading". 

Workaround: **HP protection tools are  rewriting to the MBR when Windows is run**. The *protecttools* app  must be removed/disabled. Refer to post #10 in the Bug Report.



From http://ubuntuforums.org/showthread.php?t=1195275

---

### Post by jsmanian on 2010-04-22
Hi [COLOR=Black]andrewthomas,

   Thanks a lot for your help. Now I can boot in both OS in grub loader:P. 

I have one clarification. I think that disabling "PC angel" is temporary solution. There is any bug fixing patch is available for this. I could not see in launchpad thread.

Anyway once again thank you....

with regards,
jsmanian
[/COLOR]

---

