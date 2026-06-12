---
title: "Upgrade to 10.04 halted at &quot;replacing config file /etc/default/grub with new version&quot;"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by patslap on 2010-04-30
I'm upgrading 64-bit 9.10 to 10.04.

All went as expected until terminal in upgrade manager displayed "replacing config file /etc/default/grub with new version" and upgrade has halted there for 30 minutes. 

What do I do? There is no 'cancel' button, and don;t want to reboot mid-upgrade in case it messes up system. Any ideas?

Thanks

---

### Post by eyemeansit on 2010-04-30
exact same problem here. No answer yet.

---

### Post by dino99 on 2010-04-30
i guess you have answered "yes"

have any hot keys to exit ?  Alt+ c or x or q (dont remember) or esc

---

### Post by patslap on 2010-05-01
No - there was no question re upgrade; upgrade manager tried to set grub-pc and is still frozen now some 12 hours later.

I'm backing up my home folder now as i anticipate a broken system :( 

Why has this happened with an LTS upgrade? Surely this should be more stable?

Any ideas how to kick-start the installation back in progress to avoid a system reboot mid-install? :(

---

### Post by patslap on 2010-05-01
Managed to fix: pressed CTRL-C to exit the terminal screen in the upgrade manager, then rebooted and selected fail-safe boot option. Ithen selected the option to 'clean dpkg' (or something similar) which then worked some magic, rebooted and 10.04 successfuly installed finally and now works.

---

### Post by eyemeansit on 2010-05-01
I took another route... I had already installed Kubuntu 10.04 final release on another partition, and have abandoned the 9.10 installation, except to mount it within 10.04 so I can port my settings over. I just was hoping the upgrade would go nicely so I wouldn't have to do that. Oh well.

---

