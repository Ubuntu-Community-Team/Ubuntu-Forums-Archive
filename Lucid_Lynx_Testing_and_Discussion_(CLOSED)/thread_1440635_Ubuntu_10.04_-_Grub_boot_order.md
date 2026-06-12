---
title: "Ubuntu 10.04 - Grub boot order"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ludvig1982 on 2010-03-27
How do i change Grub boot order in Ubuntu 10.04?

I want XP to be the default OS to load, and i don't want it to change when updating Ubuntu.

I had this right with ubunut 9.10, so it changed when i installed this version.

I use the 64x version of ubuntu

---

### Post by drs305 on 2010-03-27
The easiest way is for you to install *startupmanager* and select the default OS in that GUI app. Once installed, it is in System, Administration, StartUp-Manager.

For other ways, refer to the G2-Tasks link in my signature.

Added: There are several ways to set it. One is to use the exact title in the DEFAULT=" " setting of /etc/default/grub. That technique is described in section 3 of the G2-Tasks link.

---

### Post by projectigi3000 on 2010-03-30
best way to do is manually.

use the follwing command to open grub.cfg to manually alter the boot order.

```
sudo gedit /boot/grub/grub.cfg
```

once the file opens...scroll down to the boot options...its quite simple...to remove an entry just comment it out using hash.

---

### Post by bigsmitty64 on 2010-03-30
I thought you weren't supposed to edit  grub.cfg ?  in grub 2  . But instead edit /etc/default/grub then update grub and it saves it in grub.cfg

I also use startup manager. Works great!

---

### Post by Mark Phelps on 2010-03-30
> **projectigi3000 said:**
> best way to do is manually.

use the follwing command to open grub.cfg to manually alter the boot order.

```
sudo gedit /boot/grub/grub.cfg
```

once the file opens...scroll down to the boot options...its quite simple...to remove an entry just comment it out using hash.

Do NOT do this!  

The very next time an update-grub is done, that file is completely rewritten -- which is why it says clearly in the file that it is NOT to be edited.

Also, 10.04 is still in beta testing, so please post your beta-related questions to the correct forum: Development & Programmming, Lucid Lynx Test.

I will be asking the Mods to move this thread to that forum.

---

