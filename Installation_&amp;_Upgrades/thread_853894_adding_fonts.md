---
title: "adding fonts"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by vjayaraju on 2008-07-09
how can I fonts to ubuntu? I downloaded a .ttf file and the instruction attached to it says that the .ttf file should be pasted in root/usr/share/fonts. But I cannot access this file saying that you have no permission to modify contents of root

---

### Post by kostkon on 2008-07-09
> **vjayaraju said:**
> how can I fonts to ubuntu? I downloaded a .ttf file and the instruction attached to it says that the .ttf file should be pasted in root/usr/share/fonts. But I cannot access this file saying that you have no permission to modify contents of root
Just copy it to your *.fonts* hidden folder. To find it, just go to your home folder with *Nautilus* and select *View -> Show Hidden Files*.

If this folder does not exist, just create it yourself.

---

### Post by kaibob on 2008-07-09
The easiest way to install new fonts is to place them in the /home/username/.fonts directory. You will have to create this folder if it's not present. 

The following Ubuntu Wiki provides detailed instructions on the installation of fonts:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by iaculallad on 2008-07-09
On your terminal:

```
gksudo nautilus
```

and perform your cut/copy and paste method to /usr/share/fonts directory. Then, rebuild your font cache with the terminal command below:

```
sudo fc-cache -f -v
```

---

