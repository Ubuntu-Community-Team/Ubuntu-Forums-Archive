---
title: "Cannot log in after upgrade"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by Russ_H on 2013-08-21
Hi,

   After an update I had driver issues, basically it would fall back into terminal mode. I read that sometimes .Xauthority would cause problems and followed the advice, nothing changed. Eventuallally I removed all the nvidia drivers and re installed them and it sort of came back to life, except instead of going straight into the desktop it offers me a choice of "guest" or "Russ" , guest works but if I try and log into the "Russ" then it just falls back to offering me the choice of "guest" and "Russ" after the screen goes blank for 30 secs. I have tried putting the old .Xauthority back but I cannot even delete it, I just get "read only file system", I get the same message if I try and do chmod 777 on it. When I go to the networking prompt from bootup it never asks for passwords even if I am in root, is that correct?, it would never let me install anything without a password when it booted up before. Thanks in advance!

---

### Post by Russ_H on 2013-08-21
Put the old .Xauthority, I had forgotton to unmount the disk before,  back and it now drops straight into the command line "guest" works, tried reinstalling desktop but that made no difference.

---

### Post by Russ_H on 2013-08-21
.Xauthority is controlled by root when it falls back into the login screen on startup but if I change it to "russ" then it will go straight to command line.


Part of the graphics seems to be working as there is a mouse pointer similar to the one in low res mode but the whole screen is black.

---

### Post by grahammechanical on 2013-08-21
I am a little bit confused.

Did you have automatic login set so that you did not need to enter a password to get to a desktop? If we do not have automatic login activated we always get a login screen that will give us an option to login as the user we are or as guest or any other user we have set up. You may be seeing something that is normal. 

Sometimes when the login is broken, perhaps the password is incorrect, we get bounced back to the login screen. That is usual procedure. You may have changed the password for "Russ" and that is why you are getting this bounce back.

Furthermore, when we use Recovery Mode and select Network = Enable Networking, the script reads the Network Manager configuration file and makes the correct network connections without the need for a password. During a normal boot we are not asked to authenticate (password) a network connection. Not once we set up all the necessary details which Network Manager stores. This also sounds normal to me.

Running Recovery Mode>Network puts the file system into read/write mode which means we can edit files. Even when we select Root = Drop to a root shell prompt, the file system is still in read only mode. We need to run a command to put the file system in read/write mode otherwise we cannot even run updates.

When I have used Recovery Mode I simply run Network and then run Root and then I can update the OS and edit configuration files. Often I just do Recovery>Resume and that often gets me to a desktop without using a proprietary video driver and from there I use additional Drivers to experiment with getting a video driver that works.

So, I am not sure if what you are experiencing is normal or just something not experienced before and that the issue of a buggy video driver has now become a password issue.

Regards.

---

### Post by Russ_H on 2013-08-21
Its nothing to do with the password as it accepted it, it just dropped back to the login screen afterwards. It seemed to be connected to .ICEauthority which was set to root owner instead of me, however changing the permission did not allow the login to work with Ubuntu desktop, it now has a command line editor, a black screen and a large mouse pointer that looks like the one when low graphics mode starts. I deleted .Xauthority and .ICEauthority as these can cause problems and are recreated if they are not there by the xserver, however it still has the same problem. The driver is working as it works on the other guest login, its likely a video setup corruption but where?

---

### Post by Russ_H on 2013-08-21
Changing to gdm did not work, it just hangs and I have to reboot it. Any ideas outhere gratefully received!

---

### Post by steeldriver on 2013-08-21
Apologies if I missed it but what version and what desktop session? If it is ubuntu-3d are you able to try a different desktop session from the dm screen e.g. ubuntu-2d or xfce4? That might narrow it down

---

### Post by Russ_H on 2013-08-21
xserver reinstalled, no change.

---

### Post by Russ_H on 2013-08-21
Thanks, just tried 2D and that worked!. Have been tearing my hair out over this one!

---

### Post by Russ_H on 2013-08-21
However its saying the display is a 7" Samsung not a 40" one so I dont think its quite there yet

---

