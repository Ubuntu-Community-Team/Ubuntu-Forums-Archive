---
title: "Installation Problem - Graphics card could not be detected correctly"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by atough on 2010-12-22
Hello to all!
 
This morning i installed Ubuntu 10.10 on my Sony Vaio E Series computer. 
When I boot Ubuntu, a graphical user interface does not appear. Only a command line appears. It says:
 
Ubuntu 10.10 "alex" tty1
alex login:
 
After I log in, to shut down I use sudo shutdown now. Once I enter that in the command prompt the command line disappears, and a warning message appears, saying:
 
-Ubuntu is running in low graphics mode-
Your screen, graphics and input device settings could not be detected correctly. You will need to configure these yourself.
 
From here, I try to troubleshoot the problem, but after a few seconds the mouse and keyboard stop working. 
 
How can I fix this problem? I don't know if this problem has anything to do with the fact that I installed Ubuntu without an internet connection.
 
Thank you, and happy holidays!
 
Alex

---

### Post by oldfred on 2010-12-22
Welcome to the Forums.

Yes, it is better to install with a hardwire Ethernet connection as then it can download any special drivers for your specific system. Only if you have a generic system will it work without the additional updates. I have to download Nvidia drivers for my system. But the standard install has over 30 different video drivers as defaults.

Can you get to System, Administration, Hardware drivers?

I do not know the exact drivers you may need, but you can often installed from the command line.

Can you boot the recovery mode?

---

### Post by atough on 2010-12-22
Thank you for responding oldfried.
 
I can't get  to System, Administration, Hardwire drivers. When I do ls at the command line all that appears is examples.desktop. I don't how to access System, Administration from the command line. 
 
How can I get into recovery mode without GRUB?
 
Thanks again :) ,
 
Alex

---

### Post by oldfred on 2010-12-22
If you are only getting command line you cannot get to System as that is part of the gui.

Recovery mode should be the second menu item on the grub menu. If you have only Ubuntu or grub did not find any other systems, you may not get the menu. Then you have to hold down the shift key from BIOS until menu appears.

Recovery mode should give some options to update.

---

### Post by ppv on 2010-12-22
Can you try this at the command line after logging in 

sudo dpkg-reconfigure -phigh xserver-xorg

startx

---

### Post by atough on 2010-12-22
Hello to both,
 
I tried sudo dpkg-reconfigure -phigh xserver-xorg the startx to no avail.
 
I managed to access the BIOS. I updated, but the problem is still there.
 
I'll be getting a hardwire Ethernet connection in January. I will try to update then, and in the worst case I'll reinstall Ubuntu with the Ethernet connection.
 
Thank you all :)

---

