---
title: "Splashscreen Swapped"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by Tlon on 2008-06-25
I've just upgraded from Gutsy to Hardy.  The upgrade went surprisingly well, with no real problems that I've yet discovered.  The one odd thing with the install is that my Xubuntu splash screen (the screen with the loading bar animation) has been replaced by the Kubuntu screen.  Now that I think of it, I may have installed from Kubuntu way back in the day, and just forgot about it; I run AMD64, so this is the first time that I've actually HAD a splash screen.  Could anyone be so kind as to tell me how to replace the Kubuntu splash with its Xubuntu equivalent?

---

### Post by Partyboi2 on 2008-06-25
You could try
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by Tlon on 2008-06-27
Tried this... oddly, it changed the one that displays briefly when the system shuts down, but left the startup splash as kubuntu.

---

### Post by Partyboi2 on 2008-06-27
try again
```
sudo update-alternatives --config usplash-artwork.so
```and after choosing "/usr/lib/usplash/usplash-theme-xubuntu.so" try
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

Or try removing kubuntu-artwork-usplash package in case it is still there.
```
 sudo apt-get remove kubuntu-artwork-usplash
```

---

