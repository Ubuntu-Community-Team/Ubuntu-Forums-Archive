---
title: "after update to lucid-beta1 no 3d support with r300 chipset"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tekknokrat on 2010-04-06
After Lucid update from Karmic I tried with getting the opensource radeon driver to work for r300. But there seems to be an issue with loading the glx extension.

Laptop model HP Touchsmart tx2.

The Xorg log shows:

```
(II) LoadModule: "glx"
(WW) Warning, couldn't open module glx
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (module does not exist, 0)

```

Full log is attached here:

 - [http://pastebin.com/vj85ftPg](http://pastebin.com/vj85ftPg)

```
$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.7.6-2ubuntu1
```

---

