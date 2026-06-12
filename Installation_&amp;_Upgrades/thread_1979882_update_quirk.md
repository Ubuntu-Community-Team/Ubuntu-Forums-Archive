---
title: "update quirk"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2012-05-14
My Inspiron 1150 laptop with a Celeron CPU and 1 gig memory was working fine with Xubuntu 10.10 until I updated software at the software manager's suggestion. Most of the additions seemed to be related to Firefox. Anyway, now it doesn't shut down in one step. It goes to a blue screen where I have to select a user and hit another shutdown button. Not a big problem just an annoyance but does anyone know how to fix it?

---

### Post by sudodus on 2012-05-14
> **Lloydb39 said:**
> My Inspiron 1150 laptop with a Celeron CPU and 1 gig memory was working fine with Xubuntu 10.10 until I updated software at the software manager's suggestion. Most of the additions seemed to be related to Firefox. Anyway, now it doesn't shut down in one step. It goes to a blue screen where I have to select a user and hit another shutdown button. Not a big problem just an annoyance but does anyone know how to fix it?
It is common that upgrading to a newer version causes problems, that might need some tweaking. I don't know about your particular problem, but if you like terminal commands, you can try ```
sudo poweroff
``` which might be more convenient than the two step path you have now.

Otherwise, download Xubuntu 12.04 and try it live from a CD or USB drive! I guess you upgraded to 11.04 now (and it lasts one half a year until end of life). It would take two more steps to upgrade to the current and LTS release, so unless you have a lot of special programs and tweaks, it will save time and effort to backup your personal data, do a clean install, and restore your data into the new environment.

---

### Post by Lloydb39 on 2012-05-21
Just so I understand: Do I just save my home folder on a jump drive and move it back after the new install? Does that restore all my files and settings?

---

### Post by raja.genupula on 2012-05-21
Yeah , take backup of your Home folder and then restore it get your previous settings.

---

### Post by sudodus on 2012-05-21
> **Lloydb39 said:**
> Just so I understand: Do I just save my home folder on a jump drive and move it back after the new install? Does that restore all my files and settings?
It is not quite that simple because the versions are different. Many settings would be the same, but others won't. Maybe you can get some help reading some posts by *oldfred* about home partition, for example this one
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11945121&postcount=18_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11945121&postcount=18")

---

