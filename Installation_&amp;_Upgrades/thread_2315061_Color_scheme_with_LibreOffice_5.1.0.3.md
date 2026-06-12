---
title: "Color scheme with LibreOffice 5.1.0.3"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2016-02-25
Very recent upgrade of LibreOffice 5.1,0.3 has given some very strange colors for toolbars, drop-down menus.  I have not changed anything on my PC's, but now for example, labels on the tabs under FORMAT CHARACTER are in white-colored font on a light-gray background.  Main menu area uses white-colored font on dark-gray (black?) background.  This has occurred over multiple PCs.

How do I get back to a decent color scheme?

Thank you,

John

---

### Post by vasa1 on 2016-02-25
Please provide the output of: 
lsb_releases -a
uname -r
dpkg -l libgtk2.0-0 libgtk-3-0
env | grep XDG_CURRENT_DESKTOP
echo $DESKTOP_SESSION
ls /etc/profile.d/


Also, do you have these files?
```
08:00 AM ~ $ apt-cache searchlibreoffice | grep gtk
libreoffice-gtk3 - office productivity suite -- GTK+ 3.0 integration
libreoffice-gtk - office productivity suite -- GTK+ integration
08:01 AM ~ $ 

```

Thanks!

Edit:while not directly related, do look at [http://askubuntu.com/questions/732483/libreoffice-gtk3-and-lubuntu-14-04-lts](http://askubuntu.com/questions/732483/libreoffice-gtk3-and-lubuntu-14-04-lts) including muru's comments.

---

### Post by cigtoxdoc on 2016-02-25
Thank you.  Information you requested follows:
johnl@johnl-Vostro-3500:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily
johnl@johnl-Vostro-3500:~$ uname -r
4.2.0-30-generic
johnl@johnl-Vostro-3500:~$ dpkg -l libgtk2.0-0 libgtk-3-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgtk-3-0:amd 3.18.6-1ubun amd64        GTK+ graphical user interface lib
ii  libgtk2.0-0:am 2.24.28-1ubu amd64        GTK+ graphical user interface lib
johnl@johnl-Vostro-3500:~$ env | grep XDG_CURRENT_DESKTOP
XDG_CURRENT_DESKTOP=Unity
johnl@johnl-Vostro-3500:~$ echo $DESKTOP_SESSION
ubuntu
johnl@johnl-Vostro-3500:~$ 

Please let me know if you need additional information.

John

---

### Post by vasa1 on 2016-02-25
Please also provide the output of
```
apt-cache search libreoffice | grep gtk
```

I see```
libreoffice-gtk3 - office productivity suite -- GTK+ 3.0 integration
libreoffice-gtk - office productivity suite -- GTK+ integration
```Depending on whether you're using gtk2 or gtk3, you will need the respective file.

A screenshot of what you see would also be useful.

Here's something from the [Arch wiki]("https://wiki.archlinux.org/index.php/LibreOffice#Theme"):> However, if it looks like it is using Windows 95/98 icons, go to Tools > Options... in the menus (which presents the Options Dialog), then select LibreOffice > Accessibility and uncheck "Automatically detect high-contrast mode of operating system".

If that does not work immediately, you may need to change the icon set that is in use; this is also in the Options Dialog, under LibreOffice > View with two pop-up boxes for "Icon size and style" (the latter pop-up box should be changed to something other than "High-contrast"). 

---

### Post by cigtoxdoc on 2016-02-26
johnl@johnl-Vostro-3500:~$ apt-cache search libreoffice | grep gtk
libreoffice-gtk - office productivity suite -- GTK+ integration
libgtkspellmm-3.0-0v5 - C++ wrapper library for GtkSpell (shared libraries)
libgtkspellmm-3.0-dev - C++ wrapper library for GtkSpell (development files)
libgtkspellmm-3.0-doc - C++ wrappers for GtkSpell (documentation)
libreoffice-gtk3 - office productivity suite -- GTK+ 3.0 integration
johnl@johnl-Vostro-3500:~$

---

### Post by vasa1 on 2016-02-26
Please take a look at the Arch wiki link. I edited my post after you replied, I think.

---

### Post by cigtoxdoc on 2016-02-26
Thank you for your replies.  Attached  is the screen shot from LibreOffice write showing the Format Character Menu
[ATTACH=CONFIG]267516[/ATTACH]

---

### Post by vasa1 on 2016-02-26
> **cigtoxdoc said:**
> Thank you for your replies.  Attached  is the screen shot from LibreOffice write showing the Format Character Menu
...
Ouch! That's bad. What gtk theme are you using? Have you tried some other theme? Do all your machines have the same gtk theme?
I too have Version: 5.1.0.3 and the corresponding screen looks like this for me:

---

### Post by cigtoxdoc on 2016-02-26
GTK+ theme is Ambiance.  Most critical software application is Evolution 3.18.2.  Only decent colors on that come from Ambiance.

---

### Post by howefield on 2016-02-26
Excuse me jumping in, you could try moving or renaming the folder..

```
~/.config/libreoffice/
```

If it doesn't work, you can move it back.

---

### Post by vasa1 on 2016-02-26
[https://bugs.documentfoundation.org/show_bug.cgi?id=92776](https://bugs.documentfoundation.org/show_bug.cgi?id=92776) ???

[http://askubuntu.com/questions/738141/libreoffice-5-1-doesnt-integrate-with-unity-in-ubuntu-15-10/738156#738156](http://askubuntu.com/questions/738141/libreoffice-5-1-doesnt-integrate-with-unity-in-ubuntu-15-10/738156#738156)

---

### Post by cigtoxdoc on 2016-02-26
I tried numerous changes in theme using Gnome Tweak tool, but no improvement LibreOffice and readability problems with Evolution.  I have too much urgent client work to mess with LibreOffice config files when I do not know what I am doing.   Looks like this is an intractable problem w/o a revision in LibreOffice to change font colors on tabs.

John

---

### Post by vasa1 on 2016-02-26
Did you try this?```
sudo apt-get remove libreoffice-gtk3
```If it doesn't work, you can just re-install the package.

Removing *libreoffice-gtk3* will force LibreOffice into gtk2 mode.

---

### Post by cigtoxdoc on 2016-02-27
Thank you vasa1.  You have provided the correct answer.  Removing libreoffice-gtk3 solved problem.

John

---

### Post by vasa1 on 2016-02-27
Glad I could help :)

---

