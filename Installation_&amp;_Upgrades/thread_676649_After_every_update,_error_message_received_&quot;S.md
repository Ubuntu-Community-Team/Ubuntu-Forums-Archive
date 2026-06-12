---
title: "After every update, error message received &quot;Strongswan ...&quot;"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by flyingtiger on 2008-01-24
After every security update or program update I received this message "E:strongswan: subprocess post-installation script returned error exit status 1". Is this something I should be overly concerned about? Is there something I can do to fix whatever strongswan is so that the error messages cease? Running V7.10 Ubuntu.

Thanks for any assistance.

---

### Post by p_quarles on 2008-01-24
Here's info on Strongswan:
[http://packages.ubuntu.com/gutsy/net/strongswan](http://packages.ubuntu.com/gutsy/net/strongswan)

As for getting rid of the error message: it sounds like it's a broken package that failed to install. You could try fixing it. In a terminal run:
```
sudo dpkg-reconfigure strongswan
```
If that works, great. If not, make a note of whatever it tells you about *why* it didn't work.

If you don't need this package, you could also simply try uninstalling it.

---

### Post by flyingtiger on 2008-02-03
Thanks, I tried to re-install strongswan and received the same error message. So I decided to uninstall it. I am not sure if I need to have this program running on my PC. Again thanks for you help.

---

