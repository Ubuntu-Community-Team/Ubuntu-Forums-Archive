---
title: "Upgrade to Edgy &amp; lost standard splash screen"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by PhilOSparta on 2006-12-16
I just upgraded from Dapper to Edgy and the standard splash screen no longer appears.  Instead, I get what looks like a test pattern.

Any ideas?  This is strange.

A second issue related to the upgrade is that the boot frequently freezes at the current spot
on the splash screen.

Phil

---

### Post by deangl on 2006-12-28
In Synaptic I searched for "usplash".
I found that "usplash-theme-ubuntu" and "xubuntu-artwork-usplash" were "not installed" so I marked them for installation, and clicked Apply.

After exiting Synaptics, I rebooted and noticed on the shutdown the new splash screen.  Also, it worked on startup.

Try this and see if you have similar results...

Thanks,
Dale    :-)

---

### Post by amo-ej1 on 2006-12-28
indeed that should solve your problem. 

If something freezes or seems to freeze try to append 'nosplash' as a kernel parameter in grub, that way you should be able to see the output messages of what the pc is doing and 'where' it is freezing.

Or check /var/log/messages and search for 'huge' differences in the timestamps between succeeding lines.

hth

---

### Post by PhilOSparta on 2006-12-31
> **deangl said:**
> In Synaptic I searched for "usplash".
I found that "usplash-theme-ubuntu" and "xubuntu-artwork-usplash" were "not installed" so I marked them for installation, and clicked Apply.

Thanks.  I loaded "usplash-theme-ubuntu" rebooted and now the normal splash screen is visible.

---

