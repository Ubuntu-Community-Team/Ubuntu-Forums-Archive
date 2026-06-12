---
title: "ubuntu 10.04 booting problem"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by keencad on 2013-06-12
Hello all.
I have a special Bluetooth device running Ubuntu 10.04. I was installing Firefox, g++-4.7 , ... suddenly some of my applets on main menu gone and my preferences menu item's gone. I restarted device and it did not load again! grub works fine. But this is what i see when turn on device :
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 75674/1921360 files, 501891/7679062 blocks (check after next mount)
*starting AppArmor Profiles
Skipping profile in /etc/apparmor.d/disable : usr.bin.firefox

*Setting sensors limits                                         [ OK ]
*Starting Remote Desktop Protocol server               [ OK ]
*Starting web server apache2                              [ OK ]

and it will stay over here for ever.
what can i do to recover system?

---

### Post by grahammechanical on 2013-06-12
You say Grub works fine. So, have you tried booting into Recovery Mode? Have you tried booting into a Previous kernel? I would guess, from the disappearance of applets and menu items that Compiz has crashed. Did the installation of those packages finish? Were they installed? Or did you restart before that and now you have a broken system? You will have to be quick about fixing this because 10.04 has reached End Of Life but the repositories are still open for a little while longer. I installed 10.04 a couple of days ago for a test and I was able to run an update after installation. Soon those repositories will be closed and moved into an archive. Think about re-installing.

Regards

---

### Post by keencad on 2013-06-13
Dear grahammechanical
Thanks for your quick reply
Actually i was installing g++-4.7 and failed to get some packages. I think it was the reason that system crashed! As i said before i can get in Recovery mode but i don't know how to boot into previous Kernel. I did some Google search for a couple hours but i did not understand how to do that. I wonder if you could tell me how to do it or give me some references?

kind regards

---

