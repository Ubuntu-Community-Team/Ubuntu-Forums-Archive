---
title: "[SOLVED] No graphical interface after updates - please help!"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Slimo on 2008-02-06
I recently installed Ubuntu 7.10 and it worked fine on first boot.  I then downloaded and installed all 186 updates and enabled the restricted nvidia driver.  However, after rebooting, I do not get the normal ubuntu login screen...there are about 4 lines of text on screen, and by using shift+f4, f5, etc, I can get to a screen that has a line of text asking for my name and password.

Anyway, I tried editing xorg.conf using nano in this text-based screen, didnt help.  Restarted a few times and restored xorg.conf but still the same thing happens...any ideas?  Everything seemed to be working fine before the updates....or is it more likely to have been the restricted driver?

Any help would be appreciated!!  Cheers

---

### Post by taurus on 2008-02-06
Log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And if it asks you to pick a driver for your graphic card, pick either **nv **or **vesa**.

What model is your nvidia card?

---

### Post by Slimo on 2008-02-06
Thanks for your reply!

I did try changing the graphics card driver to nv and restarting, but the same problem occurred.  

I will try to reconfigure again - I did try that command previously but then the configuration options didn't appear on screen.

I have a GeForce 8600GT at the moment...however a friend of mine was saying that maybe ubuntu was using the onboard graphics instead and this was causing a problem....thoughts?

Thanks again!

---

### Post by taurus on 2008-02-06
If you have an onboard graphic controller, go into the BIOS and turn it off.  Then, Ubuntu will use the add-on nvidia graphic card.

---

### Post by Slimo on 2008-02-07
Thanks guys - seems to be working fine after I disabled the onboard graphics via the BIOS.  Am currently using the "nvidia" driver as it seems to work better than "nv"

---

