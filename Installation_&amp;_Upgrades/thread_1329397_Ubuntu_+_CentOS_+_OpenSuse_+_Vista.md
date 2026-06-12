---
title: "Ubuntu + CentOS + OpenSuse + Vista"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by manav_1001 on 2009-11-17
Hello ppl,

I had Ubuntu, CentOS and OpenSuse installed on my system and all 3 were booting up fine. But yesterday I installed Vista on another partition on the same hard drive and now when I start my computer, it takes me straight to Vista. Can anybody tell me how I can boot into Ubuntu or CentOS and uninstall Vista as I no longer need it. 

FYI: CentOS was installed on a primary partition and Ubuntu and OpenSuse were on logical partition. I dont remember if I installed Vista on a logical or a primary partition. 

Any help would be greatly appreciated. 

Thanks.

---

### Post by raymondh on 2009-11-17
> **manav_1001 said:**
> Hello ppl,

I had Ubuntu, CentOS and OpenSuse installed on my system and all 3 were booting up fine. But yesterday I installed Vista on another partition on the same hard drive and now when I start my computer, it takes me straight to Vista. Can anybody tell me how I can boot into Ubuntu or CentOS and uninstall Vista as I no longer need it. 

FYI: CentOS was installed on a primary partition and Ubuntu and OpenSuse were on logical partition. I dont remember if I installed Vista on a logical or a primary partition. 

Any help would be greatly appreciated. 

Thanks.

When you installed Vista, it overwrote the MBR with its' own bootloader.  You need to re-install GRUB, or whatever bootloader you were using to control the previous 3 linux distros.

[Here's a link for GRUB legacy]("http://ubuntuforums.org/showthread.php?t=224351").  I don't know if you are using 9.10 which uses GRUB2.  That is a different version.

You must have installed Vista in a primary partition (as it requires) and you must have the boot flag on it (as it also requires).

Back-up and regards,

---

### Post by raymondh on 2009-11-17
> **manav_1001 said:**
>  Can anybody tell me how I can boot into Ubuntu or CentOS and uninstall Vista as I no longer need it.

Use a liveCD and in live session access gparted (system > admin > partition editor).  use gparted to delete the Vista install and resize any existing partition.  Afterwards, you have to re-install GRUB also, again using the liveCD (see link in previous post)

Have a read at the [gparted documentation]("http://gparted.sourceforge.net/larry/generalities/gparted.htm").

Have a working back-up always before using a partitioning tool.

Regards,

---

### Post by manav_1001 on 2009-11-17
Thanks for your reply raymondhenson. I was very impatient and before you replied I tried to reinstall ubuntu in the same partitition as before and delete the vista partition in the process. The installation took me upto 88% and there was some problem and it took me to a Live Session. When I rebooted I got some kind of boot error..........Anyways I just installed a fresh copy of Ubuntu and will be installing CentOS and OpenSuse now.

---

### Post by raymondh on 2009-11-17
> **manav_1001 said:**
> Thanks for your reply raymondhenson. I was very impatient and before you replied I tried to reinstall ubuntu in the same partitition as before and delete the vista partition in the process. The installation took me upto 88% and there was some problem and it took me to a Live Session. When I rebooted I got some kind of boot error..........Anyways I just installed a fresh copy of Ubuntu and will be installing CentOS and OpenSuse now.

Post back if you need further assistance. 

Regards,

---

