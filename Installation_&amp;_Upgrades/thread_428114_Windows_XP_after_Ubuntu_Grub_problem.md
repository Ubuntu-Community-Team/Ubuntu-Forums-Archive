---
title: "Windows XP after Ubuntu Grub problem"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by postalservice14 on 2007-04-30
Hey everyone,

I install ubuntu 7.04, then install Windows XP.  Grub worked perfectly so I could dual boot windows and Ubuntu.  Then I upgraded XP to Vista and Vista wiped out my grub and now only boots to Vista.  Is there a way I can reconfigure Grub to dual boot again?

Thanks,

John

---

### Post by neouser99 on 2007-04-30
yes there is.

grab an ubuntu disk, boot into the system restore (or kde if it's the non-server version), mount your boot partition, and run grub-install :)

that might be a lot of information in a very little post. if it makes sense, knock yourself out, otherwise check [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") out.

don't give up hope, this is something that can be fixed :)

-neo

---

### Post by Scheater5 on 2007-04-30
Instructions courtesy of another forum regular, Bulldog.


Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter.


sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


setup (hd0)

Finally exit the grub shell


quit

That is it. Grub will be installed to the mbr.

---

### Post by postalservice14 on 2007-04-30
> **Scheater5 said:**
> Instructions courtesy of another forum regular, Bulldog.


Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter.


sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


setup (hd0)

Finally exit the grub shell


quit

That is it. Grub will be installed to the mbr.



Awesome!  thanks a bunch, worked like a charm!

John

---

### Post by Scheater5 on 2007-05-01
Good deal.  Glad to help, but Bulldog is the guy who taught me how to do that, so if you see him around the forums perhaps thanks are in order to him, too!

---

