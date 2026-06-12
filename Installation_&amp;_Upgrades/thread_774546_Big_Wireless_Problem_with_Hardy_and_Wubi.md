---
title: "Big Wireless Problem with Hardy and Wubi"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by datamichael on 2008-04-29
I have a compaq laptop, presario r3000. I've wanted to run ubuntu on it for quite some time. Every time a new release comes out, I try the live CD version. The wireless (broadcom) never works. There's lots of info on how to make it work, but I've never been successful.

I downloaded the final hardy iso, burned it to disk and fired it up. Low and behold the wireless works! An icon appears next to the username in the upper right corner saying new drivers are available. I click enable for broadcom and then asks me to install fw-cutter. I say ok and after a few minutes it's done and I can see and connect to wireless networks. Works great! Well done!

Eh, not so fast....

Feeling the the ubuntu gods have finally smiled on me, I install via wubi. No problems during the install. However, when it finished I don't get the "new driver" icon. When I go to the hardware drivers panel, the only choice is Nvidia. No broadcom driver found.

So, it works with the live CD. So I FINALLY know it can work. But it doesn't work with wubi install.

Any help? Anyway to do it SIMPLY????

Thanks!

---

### Post by apurgert on 2008-04-29
Have you tried this guide yet?  It worked for me, but the only thing I had to change was the "$FIRMWARE_INSTALL_DIR" in the last command (../../b43-fwcutter-011/b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” wl_apsta) to /lib/firmware with no quotes.  Can't remember if you have to sudo, never hurts to do so.  I think that's about it, I don't have my laptop in front of me and I am on a M$ computer at work.

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

Hope that helps.

---

