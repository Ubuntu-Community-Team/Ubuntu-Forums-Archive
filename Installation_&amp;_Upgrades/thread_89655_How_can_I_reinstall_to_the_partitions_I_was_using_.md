---
title: "How can I reinstall to the partitions I was using before?"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by bryant8 on 2005-11-13
Hi I'm a new ubuntu user. I was uninstalling python 2.4 via synaptic when it actually removed lots of applications associated with it or something (300mb+ worth).

When I logged out I don't have access to a GUI anymore too.

How can I uninstall ubuntu completely and reinstall it? Coz if I just reinstall the desktop, other components which were removed might not be there. I'm using the Grub Loader dual booting with windows.

Please advise as I would like to clear/uninstall the ubuntu files in ubuntu partitions, then install into the same partitions, without the setup program asking to create/delete partitions again. Is there a function within that setup program which allows you to reinstall and choose which partitions to use? 

Thank you.

---

### Post by Xian on 2005-11-13
[QUOTE=bryant8]Please advise as I would like to clear/uninstall the ubuntu files in ubuntu partitions, then install into the same partitions, without the setup program asking to create/delete partitions again. Is there a function within that setup program which allows you to reinstall and choose which partitions to use? [/QUOTE]
Yes, but you will need to tell the installer to reformat the Ubuntu partition. This is not the same a creating/deleting. You will choose the manual partition option, select the Ubuntu partition, highlight the line that talks about keeping the current data, and then change that to 'format' using your desired file system.

---

### Post by bryant8 on 2005-11-13
Ok I will go try it out and let you know when I'm done. =)

Probably in an hour's time -_-

Thank you.

---

### Post by bryant8 on 2005-11-13
Ok I reinstalled it and everything's working now =)

But now partitions associated with windows appear on my ubuntu desktop. I right-clicked and tried unmounting them but it says I need to be a root user. So I logged out and tried logging in with root, but it says I cannot login from a GUI. How and where do I log in then? or what commands do I have to use?

Thank you.

---

### Post by aysiu on 2005-11-13
[QUOTE=bryant8]Ok I reinstalled it and everything's working now =)

But now partitions associated with windows appear on my ubuntu desktop.[/quote] Are you using KDE? I wonder why they're appearing on your desktop... There used to be a setting in Gnome for putting them on or taking them off, but I can't seem to find where it is. There's definitely a setting for that in KDE, though.

> I right-clicked and tried unmounting them but it says I need to be a root user. So I logged out and tried logging in with root, but it says I cannot login from a GUI. How and where do I log in then? or what commands do I have to use?

Thank you. It's probably because they're not mounted but just appearing. Do you want them to mount?

---

