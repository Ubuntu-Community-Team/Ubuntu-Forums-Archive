---
title: "Uninstalling grub after Acer Recovery"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by Smu on 2007-08-02
Hi!

I don't know if this is the right section for my problem but here it goes. I've got a acer laptop that I've had ubuntu installed on, but now I want to sell it and therefore I've used my Acer recovery CDs to get windows back on the computer.

Everything seemed to go fine, but now I'm stuck with a GRUB - error 17 and can't boot into windows. I've tried using the Live CD and running *sudo apt-get remove grub* but apparently that had no effect. Before I used the recovery CDs i used the Live CD to format the harddrive so I don't really understand where grub comes from...?

---

### Post by be4truth on 2007-08-02
The Grub sits in you MBR Master Boot Record which does not get deleted when you clean the drive. There was a copy of your old MBR in you /boot directory but that is probably gone by now. I am not familiar with the acer recovery but if you have a XP CD around 

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console")

There is a good chance that the Acer stuff get lost with this. Otherwise study you Acer documentation. You could as well contact them and ask for help. Crashed OS are common.

---

### Post by merlinus on 2007-08-02
This may help:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

-merlin

---

### Post by be4truth on 2007-08-02
Cool website!

---

### Post by Smu on 2007-08-03
Thanks for the replies! Got it finally working after many tries and multiple times formating the harddrive... So does anyone want to buy a crappy acer laptop with XP home? ;)

---

