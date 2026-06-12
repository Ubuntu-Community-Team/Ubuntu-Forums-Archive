---
title: "Ubuntu 14.04 LTS desktop on a virtual machine"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by shadin2 on 2014-08-24
I have a running Ubuntu 12.04 LTS desktop on a virtual machine. I wanted to upgrade it to 14.04 but I got this warning:

```
Your graphics hardware may not be fully supported in Ubuntu 14.04


```

When I checked the link: [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D)
It says this could happen because of Virtual machines.
I can wait for now but my question is, is this permanent or would be supported soon?

---

### Post by ibjsb4 on 2014-08-24
I do not see this changing anytime soon.  If you want to stick with the Unity desktop then stick with 12o4.  12o4 is supported till 2017, maybe by then things will be better.

If you want to move on to 14o4, you could give [Xubuntu]("http://xubuntu.org/") a try.

---

### Post by lah7 on 2014-08-24
Unfortunately, Unity isn't designed nor optimised for use inside a virtual machine due to the fact it renders in 3D (it's a compiz plugin). It will come with a massive performance penalty.

Other desktop environments are recommended. Whether it's an official flavour or simply installing additional desktop packages.

---

