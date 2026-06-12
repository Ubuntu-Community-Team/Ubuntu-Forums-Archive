---
title: "Nvidia driver now fixed"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2010-03-06
[B]The problem is solved now and you can safely use driver 195.36.15 if you like.
[/B]
[From Alberto Milone on the Ubuntu Foundations Team]

Hi all,

According to Nvidia, drivers 195.36.08 (i.e. the current driver in the archive) and 195.36.03 might be affected by the same GPU fan speed issues which affect the Windows driver:
[http://www.nvnews.net/vbulletin/announcement.php?a=39](http://www.nvnews.net/vbulletin/announcement.php?a=39)

I have been using these drivers for while now without experiencing that problem but, if you want to be on the safe side, I suggest that you temporarily switch to the open driver until we're sure that the problem is fixed. In order to do so you can follow either point 1 (the easy way) or point 2:

1) Disable the driver with Jockey (the restricted drivers manager) and restart your computer.

OR

2) Open the terminal and type the following commands:
```
sudo update-alternatives --config gl_conf 
```
(and select the alternative provided by mesa)
```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

and restart your computer.


Sorry for the inconvenience, I'll keep you posted on the issue.

Regards,

--
Alberto Milone
Sustaining Engineer (system)
Foundations Team
Canonical OEM Services

---

### Post by Technoviking on 2010-03-06
Please discuss here.
[http://ubuntuforums.org/showthread.php?t=1422970](http://ubuntuforums.org/showthread.php?t=1422970)

---

### Post by Technoviking on 2010-03-21
Problem new fixed.

---

