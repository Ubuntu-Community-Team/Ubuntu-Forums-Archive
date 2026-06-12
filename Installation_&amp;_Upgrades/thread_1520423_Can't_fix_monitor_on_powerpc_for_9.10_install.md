---
title: "Can't fix monitor on powerpc for 9.10 install"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by EvulNater on 2010-06-29
I have a tray-loading iMac G3 that, after installing Ubuntu 9.10 (Karmic Koala) using the alternate installation cd, will go to a blank screen after booting. I know there is a way to fix it so that the horizontal and vertical refresh rates are correct to display what I need, but once it boots to a blank screen, and i go ctrl-alt-f1, it prompts me for a user name and password. I am 100% sure that I am typing in both correctly as i set them during the alternate install process, as I've done it twice so far, and caps wasn't on and I typed and retyped them to make sure they were correct. No matter what I try (even username: root, password: root, or username: admin, password: admin) it says login incorrect. 
I saw that you can check the current user names and reset passwords by  going into recovery mode, which I read you can get into by pressing  shift or esc on boot, but on separate runs i tapped each key all the way  from turn-on to the blank screen and no such option to go into recovery  mode came up. 
Also, I try booting from the Live Installation CD, and when it boots to the blank screen, and i type ctrl-alt-f1, it gives me a neverending shower of Authentification failure's (as in they keep appearing down the screen, I can't type anything because it becomes interrupted by more Authentication errors). 
I'm at the end of my chain here. Any help would be appreciated. Either by getting me into recovery mode to fiddle with the passwords, getting it so that it takes the user name and password I set to it, or figuring out why the Live CD machine-guns me with Identification errors.

---

### Post by chkneater on 2010-06-29
I had the same problem installing 9.10 on an AMD 64 Compaq.  However, even though the screen was blank I could hear the startup sounds.  I typed my login even though I couldn't see it and it booted up.  The monitor was still blank though.  Don't know how that might help.  Also, you should select to have the GRUB menu installed in the MBR when it asks you too during installation.  That way you'll have the option to go into recovery before your screen blanks out.

---

### Post by EvulNater on 2010-06-29
Thanks for the idea, however I'm not quite sure where the option to install Grub would be. These iMac G3s seem to be pretty different from your regular Ubuntu install. Any idea what part of the install would allow me to add GRUB?

---

### Post by chkneater on 2010-09-05
it will ask you at the end of the ununtu install if you want to installl it.

---

