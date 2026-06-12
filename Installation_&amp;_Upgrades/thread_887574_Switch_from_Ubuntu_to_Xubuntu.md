---
title: "Switch from Ubuntu to Xubuntu"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2008-08-12
Hi there, my fellow Ubuntuers.

I am one of those impatient people who doesn't like to wait to download another install CD to do basically the same thing as the one I have.  Well, sometimes I do exactly that, but I just got especially impatient one day and decided to install regular vanilla (Gnome) Ubuntu on this old Compaq Presario that really can't handle Gnome very well.  The idea was that I'd just switch over to Xfce (Xubuntu) after install.  Now, I've got Xubuntu-desktop installed, but how do I get rid of the Gnome desktop?  (BTW, I know that I should keep most of the libraries, and I'd also like to keep gnome-utils and some other things, I just don't want the full desktop on there as it will never be used.)

Also, I'd like to switch the boot-splash to Xubuntu.  Please help me with that too, or point me in the right direction.

Thanks

---

### Post by tuxxy on 2008-08-12
[https://help.ubuntu.com/xubuntu/desktopguide/C/index.html](https://help.ubuntu.com/xubuntu/desktopguide/C/index.html)

---

### Post by gjoellee on 2008-08-12
click on the link below to "one click install" Xubuntu:
[apt://xubuntu-desktop](apt://xubuntu-desktop) (you might have to wait up to 15sec before the download starts)
then log out click on "sessions" on the login screen and select Xubuntu or Xfce, (I am not sure what it says) then select "Make Default" and you will never *have* to see GNOME again...

---

### Post by snowpine on 2008-08-12
Here is a good guide to uninstalling the gnome desktop: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by Nopposan on 2008-08-12
Thank you, snowpine.  I followed the link you posted and I entered the commands into apt-get, uninstalling a lot of ubuntu/gnome stuff that isn't part of xubuntu.  That helped.

I did run into one problem, however.  I get this error message re[eatedly almost every time a package is removed or installed.
```
/var/lib/scrollkeeper/en_GB/scrollkeeper_cl.xml:792: parser error : Extra content at the end of the document
le>
^
/var/lib/scrollkeeper/ca/scrollkeeper_extended_cl.xml:1478: parser error : Extra content at the end of the document
     <title>Detecció d'intrusions</title>
     ^
/var/lib/scrollkeeper/ca/scrollkeeper_extended_cl.xml:1478: parser error : Extra content at the end of the document
     <title>Detecció d'intrusions</title>

```

Does anyone know what that's about?

BTW, I am already pretty familiar with Xfce and Xubuntu, I've just never installed Xubuntu in this fashion before.  Also, as I posted in the start of this thread, I already have Xubuntu-desktop installed, so I'm not sure how the one-click install binary would be of help.

Thanks to everybody though, for your responses.  And if anyone can help me sort out that error, I'd be grateful.

Cheers!

---

