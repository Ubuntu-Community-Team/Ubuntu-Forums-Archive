---
title: "Upgrade from 7 to 8 now logon problems"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by tc3racer on 2008-06-03
Hi There.

I recently installed the new version of Ubuntu 8 i went through the installation no problem comes to the login screen and enter my right user name and password and it is rejecting it. i have not forgotten it as i use that password i entered quite a lot . I have also tried it with caps on and off. is there anyway to get past the login screen or create an new password or user name so i can get past the login screen without having to make a new installation.

Cheers:)
tc3racer.

---

### Post by tgrimley on 2008-06-03
This may be related to the sudo bug due to a bad hostname in /etc/hosts and /etc/hostname.  I'd boot into single user mode (edit the grud line, add single to the end) and check those things.  You tried to ctrl+alt+f1 to get to a login prompt and that fails too?

---

### Post by tc3racer on 2008-06-03
Hi there.

Finally managed to resolve the logon issue tried all of the treads saying try pressing ESC + e however my server was just ignoring me when i pressed ESC on boot. so i went to my last option which i thought i could do. That is to insert your Ubuntu 8 disc if you have it hand and boot it when u come to the Ubuntu menu which ask you if you would like to install on the system and all of the option select the recovery mode option. The recovery mode will then run some bits of the setup again not the whole thing though as of course its recovery mode. You will finally get the menu which asks you what you would like to repair simply select Setting Up Users And Passwords. Recovery mode will then re run part of the setup again after that it will reboot again. For those whose who use the command instead of the gui should get in as it worked for me however gui im not sure.

Hope This Helps

Cheers to the people who also replied to my thread and tried to help i tried all seggestions however pcs are pcs and they can give you the resultyou did not want sometimes

Cheers ;)

---

