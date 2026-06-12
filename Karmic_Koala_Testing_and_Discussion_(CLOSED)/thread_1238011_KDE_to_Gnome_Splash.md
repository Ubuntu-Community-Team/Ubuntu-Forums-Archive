---
title: "KDE to Gnome Splash"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-08-12
Gday folks

Not that I really care but this is bothering me a little. Since ditching my tests of Kubuntu and returning to the blessed flock of Gnome, I still get the Kubuntu splash screen despite purging all KDE I could find.

How do I reset to the Ubuntu splash?

Thanks

---

### Post by inportb on 2009-08-12
It might be helpful to have a look at the usplash-theme-* packages.

---

### Post by MacUntu on 2009-08-12
You mean Usplash? Package should be kubuntu-artwork-usplash or you can do:

```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by bacardiandwatermelon on 2009-08-12
Does KDE 4.3 work well on karmic? I just saw some screen shots and I am tempted to switch from gnome forever :-)

---

### Post by caryb on 2009-08-12
> **bacardiandwatermelon said:**
> does kde 4.3 work well on karmic? I just saw some screen shots and i am tempted to switch from gnome forever :-)

Need thumbs up emoticon

---

### Post by jbernardo on 2009-08-12
> **bacardiandwatermelon said:**
> Does KDE 4.3 work well on karmic? I just saw some screen shots and I am tempted to switch from gnome forever :-)

The "regular" plasma desktop works very well on my aspire one 110L - even the cube effect is smooth. The netbook desktop is still a work in progress, but shows a lot of promise. 
There is a open bug on knetworkmanager, as for now you have to install network-manager-gnome and run nm-applet to have wifi. But that should be fixed soon.

---

### Post by inportb on 2009-08-12
> **caryb said:**
> Need thumbs up emoticon

Absolutely.

> **jbernardo said:**
> There is a open bug on knetworkmanager, as for now you have to install network-manager-gnome and run nm-applet to have wifi. But that should be fixed soon.

Or wicd, if you don't want to mess with all the Gnome dependencies.

---

### Post by Nullack on 2009-08-12
thanks folks

---

