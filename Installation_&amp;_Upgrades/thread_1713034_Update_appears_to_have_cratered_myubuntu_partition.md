---
title: "Update appears to have cratered myubuntu partition"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by PapaC on 2011-03-23
:confused:

I have Ubuntu 10.04 dual boot with WXP

Update manager said I needed to update. 

Gave the password. 

Then it said reboot.

When I rebooted, only the XP partition would boot. 

I saw that grub was updated. Is it possible that the grub update corrupted my grub?

I can see the menu to select either WXP or Ubuntu, but when I select Ubuntu, the system reboots from scratch. 

I am booted from an Ubuntu USB key right now. I tried to mount what I think is the Ubuntu partition, but there does not appear to be anything on it. What happened?

---

### Post by Dutch70 on 2011-03-24
Hi & welcome to UF

 Please post your boot info script between "code" tags by highlighting the info & clicking the "#" in the toolbar of your next post.

Download it to your desktop, from here...
[[COLOR="Blue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")

Then open a terminal & run the following command which will produce a results.txt file on your desktop. copy/paste the results into your next post.
**Between code tags.**
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

