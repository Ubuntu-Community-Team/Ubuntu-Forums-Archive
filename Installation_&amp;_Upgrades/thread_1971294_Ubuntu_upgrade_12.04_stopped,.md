---
title: "Ubuntu upgrade 12.04 stopped,"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Genitruc on 2012-05-02
Hi everyone,

               I'm in big troubles. I tried to upgrade 11.10 to 12.04 using update manager but it stopped. The last line in the terminal is:

"Installing new version of config file /etc/dhcp3/dhclient-enter-hooks.d/samba .."

I managed to open another terminal but I have no idea what to do..?

Thanks for helping, I really need it.

Genitruc

---

### Post by Genitruc on 2012-05-02
Well.... it's work now.

     Because I had full backup and I was impatient, I took a chance an reboot. The new version was working partially and I run "dpkg --configure -a" wich finalized the installation. At some point a window prompted asking me what to do with samba's config file. After selecting one of the options the installation completed. I guess this window should have appeared during the first installation but didn't and everything had stopped waiting for me to select an option. Everithing seems to work so far, end of story.

Genitruc

---

