---
title: "Tweak Login Greeter for LightDM"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by slumbergod on 2011-10-14
After looking for ages I finally found the customisation method for the new LightDM Greeter. To save others searching I thought I would just post it here.

sudo nano /etc/lightdm/lightdm.conf

Add:
greeter-hide-users=true
allow-guest=false

(credit: [http://www.puppychau.com/archives/130](http://www.puppychau.com/archives/130))

Unfortunately, the Simple Lightdm Manager that everyone is using doesn't work with my installation of Xubuntu 11.10. I had to change the background wallpaper manually and haven't managed to change the logo at all.

---

