---
title: "Uninstalling a driver (webcam)"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by arjung on 2007-12-24
Hey all, im very new to ubuntu linux but i havent used my windows partition in almost 2 weeks now, because i love it so much.

I was having problems with my webcam so i trying several things and after searching forums etc tried installing SYNTEK drivers for my asus laptop specifically "stk11xx-1.2.3". I think i installed it by making it from the source.

This didnt solve the problem so after further searching it turned out i had a different manufacturer so i got the corrent drivers and now my webcam works fine.

After that i tried to remove the stk11xx-1.2.3 folder form my home folder and put it in trash. After a week or so i emptied my trash bin and all but this folder was deleted. I kept on getting the error that I didnt have permission to delete it.

Here is the schreenshot:
[[IMG]http://img176.imageshack.us/img176/1488/screenshotdg2.th.png[/IMG]](http://img176.imageshack.us/img176/1488/screenshotdg2.png)
 

I searched for  "k11xx" looking for this  .mod file and found only this:
[[IMG]http://img412.imageshack.us/img412/6717/screenshot1uy4.th.png[/IMG]](http://img412.imageshack.us/my.php?image=screenshot1uy4.png)


Help a newbie out plz, ty

--Arjun

---

### Post by Partyboi2 on 2007-12-24
open [SIZE=-1]Nautilus as root and try empty the trash
[/SIZE]```
sudo nautilus
```

---

### Post by arjung on 2007-12-24
didnt work

the trash folder was empty in Nautilus

---

### Post by (((X))) on 2007-12-28
code:
sudo -s
cd /home/yourname
rm -rf ~/.local/share/Trash/files

---

### Post by arjung on 2007-12-31
didnt work also..

---

