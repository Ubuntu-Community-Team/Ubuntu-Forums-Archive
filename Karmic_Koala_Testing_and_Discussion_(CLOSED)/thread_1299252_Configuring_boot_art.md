---
title: "Configuring boot art"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by blazemore on 2009-10-23
I'd like to know how to change that white logo that appears before the xsplash theme. I'd like to change it to the logo of my university, for a customised distro I'm making.
Any help would be appreciated.
Thanks!

---

### Post by blazemore on 2009-10-24
bump. I can't seem to find that logo anywhere!

---

### Post by philinux on 2009-10-24
The white logo is usplash then a gap the xsplash takes over.

I've used these commands in the past.

sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so [B]/usr/lib/usplash/usplash-theme-fingerprint.so 10
[/B]
sudo update-alternatives --config usplash-artwork.so

sudo update-initramfs -u

But cant remember the exact method. You'll have to do some digging regarding configuring usplash. I seem to remember that if you get it wrong you end up with either a blank screen or text rolling by.

---

### Post by blazemore on 2009-10-24
I know it's usplash. There must be a png somewhere, or a file you can extract to get the png?

---

### Post by philinux on 2009-10-24
> **blazemore said:**
> I know it's usplash. There must be a png somewhere, or a file you can extract to get the png?

Yep but it must be package as a .so file. This is what usplash picks up.

/usr/lib/usplash/usplash-theme-ubuntu.so. It needs to be compiled.

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto).  Bit out of date though.

---

