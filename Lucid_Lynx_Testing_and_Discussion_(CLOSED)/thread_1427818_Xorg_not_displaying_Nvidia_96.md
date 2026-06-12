---
title: "Xorg not displaying Nvidia 96"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2010-03-12
I have an older laptop I just loaded Lucid onto, after updates I booted back in and enabled the proprietary driver and rebooted.  I can now hear the Ubuntu sounds in the background, but my screen remains black.

---

### Post by forumache on 2010-03-12
After you hear login sound and see black screen, press enter.
On my computer I get again the login sound, this time with the login box displayed.

I think it is a race condition, gdm starts without a screen, them it is restarted and it manages to display image.

---

### Post by LordVeovis on 2010-03-12
> **forumache said:**
> After you hear login sound and see black screen, press enter.
On my computer I get again the login sound, this time with the login box displayed.

I think it is a race condition, gdm starts without a screen, them it is restarted and it manages to display image.


I set my PC to login without a password being required.  I do not need to type the password.  I hear the login sounds and still black.  This happened immediately after I activated the proprietary Nvidia.

---

### Post by LordVeovis on 2010-03-12
Is there a way for me to manually change the resolution by command line?  I have tried messing with the xorg.conf file, but no changes in what happens.  I don't know if I have all the stuff in it setup right, but it should be.

---

### Post by lidex on 2010-03-13
I would suggest removing xorg.conf completely. Remove all nouveau packages and all plymouth packages except the one that takes half your desktop with it. Remove any other nvidia drivers except for modaliases, nvidia-settings, nvidia-common.

---

