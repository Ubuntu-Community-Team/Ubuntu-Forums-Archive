---
title: "New Install: My AMD Catalyst Admin Settings Are Not Saved After Every Reboot"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by vincej on 2015-01-06
I just did a new install of Ubuntu onto a desktop. I have 3 monitors and an AMD 6700 GPU. I manage the 3 monitors with the AMD  Catalyst Driver. I have set the primary screen using the Ubuntu display dialogue. It all works well. However, every time I do a reboot the settings are lost  and it reverts back to a single monitor set up with the other two monitors are simple mirrors.  

This never happened on the old install of Ubuntu and the old install of AMD Catalyst. 

Any ideas ?

---

### Post by yancek on 2015-01-06
If you did an actual full install of Ubuntu onto a hard drive, there is not reason that should be happening.  The behavior you describe is expected if you were using Ubuntu installed to a flash drive or installed with something like unetbootin or pendrivelinux.  Are you able to go into System Settings and make and save change or do you get any warning/error messages when doing it?

---

### Post by vincej on 2015-01-06
I did a fresh install onto an ssd. It was previously installed on an HDD. 

I can change and save my background no problem.

---

### Post by MAFoElffen on 2015-01-06
Which flavor Ubuntu? Gnome or Unity?

Why did I ask that? I have 7 desktops here. One of those 7 has this problem, but only in Gnome 3. If I switch that one to Gnome Metacity, Gnome Compiz, Gnome Classic or Unity, it takes the setting from my xorg.conf. It I use Gnome 3 on that one it ignore's the server layout and resolutions. 

That one is nVidia (different GPU than yours) and multiple monitors. I can set it via NVidia setting or Display settings... but on reboot, ignored. I haven't had time to trace that down on mine, so just set everything up in a script to xrandr settings, triggered from startup applcations (X.destop file.) 

Mine is specific and narrowed down to Gnome3. Will follow this thread, but taking care of others issues and a 25 credit course load...

---

