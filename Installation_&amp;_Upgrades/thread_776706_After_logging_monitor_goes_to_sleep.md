---
title: "After logging monitor goes to sleep"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by kennycason on 2008-04-30
I just installed Ubuntu 8.4 on my mothers HP desktop
When I log in the monitor goes to sleep, then when the screen comes back on its back at the login screen.
the monitor is a HP pavilion vf15

I tried going to the command line and editing the etc/usplash.conf by changing the xres anad yres to resolutions that the monitor supports:
found at this site -> [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00041857&lc=en&cc=us&dlc=en&product=348762](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00041857&lc=en&cc=us&dlc=en&product=348762)

it says in the usplash.conf file that the changes will only be applied after running update-initramfs. im not really sure what that implies doing, but i ran sudo update-initramfs -u then tried relogging in.
i tried various resolutions. no luck. 
I am beat as how to fix this. Thanks.

---

### Post by kennycason on 2008-05-02
anyone have any ideas?

---

### Post by Ptero-4 on 2008-05-02
You have to run that command in the terminal (use ctrl-alt-f1 to get there) as root using sudo.

---

### Post by kennycason on 2008-05-02
I did that with no problem. but still no success. Thanks for the reply.

---

### Post by kennycason on 2008-05-04
anymore ideas? If I can't resolve this in 2 days, I have to re-install Windows.

---

