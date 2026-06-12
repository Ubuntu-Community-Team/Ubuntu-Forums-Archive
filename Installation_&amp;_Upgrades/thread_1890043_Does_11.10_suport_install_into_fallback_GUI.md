---
title: "Does 11.10 suport install into fallback GUI?"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by ubix on 2011-12-02
I am planning to install new 11.10 (Oneiric). I am not sure if my graphics is good enough for Unity (GNOME3), and would like to know if there is an option during installation to install into fallback GUI.

---

### Post by mikewhatever on 2011-12-02
There is no option to install Gnome fallback during the installation. You'll get Unity2d if the graphics card can't handle Unity, and of cause, would be free to install Gnome fallback afterwards.

---

### Post by ubix on 2011-12-02
Will not this cause the installation to fail and not install everything else?
I suppose I will have to be in the text mode in order to install the fallback with 
```
apt-get install gnome-tweak-tool
```

Am I right, or perhaps installation does complete even if it fails?

---

### Post by mikewhatever on 2011-12-02
Both gnome fallback and gnome-tweak-tool are not part of the default 11.10 installation, thus, no, the installation should not fail. When 11.10 is installed, you can use either the Software Center or a terminal window to install other packages.

---

### Post by ubix on 2011-12-02
Thank you! In your earlier reply I missed your comment about **Unity2D**

---

