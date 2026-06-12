---
title: "Problems after 10.10 upgrade"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by Lucas Malor on 2011-11-05
Background: I updated from 10.04 to 10.10 with the cdupgrade script (I mounted the cd iso).

[LIST=1]
[*]The biggest problem is I can't login with "Gnome Classic", but only with Unity (2d or 3d). And I **HATE** Unity.

I noticed these errors:
[LIST]
[*]during update:
```
Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 111
```
[*]at bootstrap:
```
udevd[487]: failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:00:02.0/usb2/2-4 2 2': No such file or directory
```
[*]in Xorg.log:
```
[   150.251] (EE) Failed to load module "nouveau" (module does not exist, 0)
```
[/LIST]

How can I solve these problems and disable Unity?

[*]I noticed Libreoffice was not updated. Is it no more in ubuntu cd? I installed it with debs from [http://www.libreoffice.org/](http://www.libreoffice.org/) since PDF extension didn't work with Ubuntu version.
[*]Finally, I noticed some settings was resetted:
[LIST]
[*] auto-login with my account was disabled
[*] desktop background was resetted
[*] autoplay was re-enabled
[*] recent documents was re-activated
[*] drivers for canon mf4120 (downloaded from [Canon site]("http://translate.google.com/translate?sl=it&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fwww.canon.it%2FSupport%2FConsumer_Products%2Fproducts%2FFax__Multifunctionals%2FLaser%2FLaserBase_MF_series%2Fi-SENSYS_MF4120.aspx%3FDLtcmuri%3Dtcm%3A80-823016%26page%3D1%26type%3Ddownload")) was unistalled
[/LIST]

 Where I can submit these bugs?
[/LIST]

---

### Post by Lucas Malor on 2011-11-10
up...

---

### Post by s.fox on 2011-11-10
Thread moved to [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333") at OP request.

---

### Post by Lucas Malor on 2012-03-25
Ok, most of the problems are gone with updates - since I have an internet connection now - and some manual work. Anyway I must say this is the worst upgrade I ever done. If I could do it easily I would downgrade to 11.04...

---

