---
title: "Photoshop CS2 asking for proper privileges"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by nichpakaich on 2008-05-04
I managed to install Adobe Photoshop CS2 by using wine, and activated it. But then, this problem occurs.

When I run Adobe Photoshop through wine, it showed a dialog box that says:
> You are not allowed to continue because your account does not have the proper privileges. Please login using an account with administrator privileges and try again.
I tried to change the permission for the file, the Adobe folder, and the chmod +w -R upon .wine folder. But all result to nothing :confused:

If anyone can help me with this, I'd be grateful.
PS:Please, don't suggest me with the portable version solution, I don't think I have the resources to do it.

---

### Post by Ticko on 2008-08-13
The same problem for me.. Any solution?

---

### Post by Lektorvis on 2008-08-15
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by CFBauer on 2008-08-15
> **Lektorvis said:**
> [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)
I don't see the permissions error covered here.  Am I missing something?

I've been running CS2 perfectly for about 6 months now, this is the first I've seen of this permissions error.

---

### Post by CFBauer on 2008-08-16
A good old fashioned reboot did the trick for me.

---

### Post by kamratwot on 2008-08-26
A reboot didnt help me.. What to do? :(

---

### Post by gabrielaca on 2008-08-26
hi, such asking for permissions comes with win-vista, there you have to rigth click and choose "run as administrator" not sure if you can do that in wine, give it a try.

---

### Post by piousp on 2008-08-26
If reboot didnt help, maybe you can try:


```

wineboot -e
wineboot -s

```

And then try again. If that doesnt help at all, try > wineconfig
to see your configuration

---

