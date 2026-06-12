---
title: "Adding XP as Dual After Ubuntu Installation?"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Tridion2000 on 2007-05-17
Is it possible to install Ubuntu and then install XP as a dual boot. After a month or so of using Ubuntu I am getting a bit fed up with it and want to return to XP. However, I'd like to dual boot for a while so install XP to a new partition but without removing Ubuntu.

Is this possible?

---

### Post by linuxmangr on 2007-05-17
Yes you can to winstall XP without remove Ubuntu .
Boot with XP format what partion you want to install XP and after the first logon on xp you need to reboot and put in drive live cd ubuntu or dvd when Ubuntu is come up you open terminal and type this :
**sudo grub**
When at the grub promt type find  /boot/grub/stage2
is return to you somthing like that (hd0,2) 
to setup boot part you need to type : root  (hd0,2) 
and after the promt you type  : setup (hd0)
ok you are ready type exit and reboot!

---

### Post by mikewhatever on 2007-05-17
Yes, it is. Installing XP will overwrite grub though, so that you pc will boot straight into XP. Here is how to restore it [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
That done, add an entry for your newly installed XP to grub menu with correct disk and partition numbers:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by Tridion2000 on 2007-05-17
Thanks for the replies. I'll give it a go over the weekend.

---

