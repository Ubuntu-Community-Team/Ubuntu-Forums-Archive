---
title: "Restore grub2 splash graphics"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by Kim Foltz on 2010-04-06
I installed Ubuntu on my system after first installing Kubuntu. Now when I boot into Kubuntu I have this garish mashup of Ubuntu and Kubuntu splash screens. They are mixed up in both the grub2 boot and the Kubuntu login.

I tried running sudo update-grub within Kubuntu but that didn't change the screens. How do I restore the default (elegant) Kubuntu splash screens?

---

### Post by Kim Foltz on 2010-04-13
The fix is to:

sudo update-alternatives --config usplash-artwork.so

sudo dpkg-reconfigure linux-image-`uname -r`

sudo dpkg-reconfigure kdm

For an explanation see [http://ubuntuforums.org/showthread.php?t=205002&highlight=splash+bug+ubuntu+kubuntu](http://ubuntuforums.org/showthread.php?t=205002&highlight=splash+bug+ubuntu+kubuntu)

---

