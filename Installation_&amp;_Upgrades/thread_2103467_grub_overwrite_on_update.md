---
title: "grub overwrite on update"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by harshatts on 2013-01-10
whenever the system ubuntu 12.10 updates the grub.cfg is overwritten to default and i have to edit and save again. is there a way around it. somehow prevent changing entries into grub.cfg file by system update.

---

### Post by sudodus on 2013-01-10
Welcome to the Ubuntu Forums :-)

> **harshatts said:**
> whenever the system ubuntu 12.10 updates the grub.cfg is overwritten to default and i have to edit and save again. is there a way around it. somehow prevent changing entries into grub.cfg file by system update.
Yes, but you have a better alternative, to edit the file
```
/etc/default/grub
```
and the files in
```
/etc/grub.d
```
instead, and run
```
sudo update-grub
```
to rewrite grub.cfg according to the new content in those files.

---

### Post by sudodus on 2013-01-10
Read more about grub here

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

---

### Post by harshatts on 2013-01-11
Thanks sudodus. 
I could change from /etc/default/grub and it updated the /boot/grub/grub.cfg to the customized settings.
 I am not sure if I will meddle with the /etc/grub.d as it seems suitable for advanced user. which i am not.

---

### Post by sudodus on 2013-01-11
> **harshatts said:**
> Thanks sudodus. 
I could change from /etc/default/grub and it updated the /boot/grub/grub.cfg to the customized settings.
 I am not sure if I will meddle with the /etc/grub.d as it seems suitable for advanced user. which i am not.

I'm glad you worked it out :KS

I think you can manage the files in /etc/grub.d too, reading those Ubuntu help pages about grub, and with a little help from the Ubuntu Forums :-)

---

