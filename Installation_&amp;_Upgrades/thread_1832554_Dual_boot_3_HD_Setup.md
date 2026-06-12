---
title: "Dual boot 3 HD Setup"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by sandman3838 on 2011-08-24
Hello everyone!  :P

I would like to setup a clean install of Win_XP, Win_7, and Ubuntu 10.04 64bit each will be on its own Separate HD .
( I was going to install 10.10 but if I understand it correctly it doesn't play well with Compiz, and I hate 11.04)    

Anyway......

Now please correct me if I'm wrong here.

Step 1 - With only the Win_XP HD connected install XP

Step 2 - Unplug the Win_XP HD and Plug in the Win_7 HD.

Step 3 - Install Win_7

** Step 4 - Plug in all the HD's with the new Ubuntu HD as the 1st in the boot order.

Step  5 - Install Ubuntu

** My question here is with step 4. :confused:
Am I connecting all the drives too soon, or should I let Ubuntu install separately by its self and let it pick up the other OS after the Ubuntu Installation?

Also, if it should come to it, let's say Ubuntu doesn't pick up the other OS's?  What in terminal should I run to get Grub 2 to pick up the other Operating Systems?

---

### Post by YesWeCan on 2011-08-24
> **sandman3838 said:**
> Am I connecting all the drives too soon, or should I let Ubuntu install separately by its self and let it pick up the other OS after the Ubuntu Installation?

Also, if it should come to it, let's say Ubuntu doesn't pick up the other OS's?  What in terminal should I run to get Grub 2 to pick up the other Operating Systems?
It is Ubuntu that plays havoc with things. So Install Ubuntu on its drive first. Then disconnect it. Connect you other drives and do your Windows installations and only then add back the Ubuntu drive. Set your bios to boot the Ubuntu drive first and once booted run
[COLOR="Navy"]sudo update-grub[/COLOR]
To add the Windows OSs and display a Grub menu.
:)

---

