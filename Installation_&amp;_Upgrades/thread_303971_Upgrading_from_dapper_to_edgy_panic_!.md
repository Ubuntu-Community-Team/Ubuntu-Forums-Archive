---
title: "Upgrading from dapper to edgy panic !"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by paratge on 2006-11-21
Hy,

I installed edgy without any error but it's looping on login screen.

I deleted .Xauthority to make it create a new one, without effect
I created a new user, without effet,
I tried acpi=force in gbub's menu.lst, without effect,
I tried acpi=off in the same one menu, without effect,
I installed again xserver-xorg without effect.

Now, I'm lost... :(

What can I do ?

Thanks in advance for your help.

---

### Post by paratge on 2006-11-21
When reboot in recovery mode and type
> sudo /etc/init.d/gdm stop
as read in another post, and type then
> startx
it crashes and must reboot.

If it can help someone to help myself...

---

### Post by paratge on 2006-11-21
So, after reading others posts, tried following things :
> sudo apt-get remove ubuntu-minimal --purge
sudo apt-get install ubuntu-minimal
and did it also for ubuntu-standard and ubuntu desktop and xserver-xorg.

Nothing make my computer work fine... always looping on login screen.

---

