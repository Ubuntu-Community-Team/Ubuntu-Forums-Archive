---
title: "Kernel upgrade installed &quot;kubuntu&quot; boot screen"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by durand on 2005-11-23
I upgraded my linux kernel yesterday using apt and it changed my boot screen from "ubuntu" to "kubuntu". I use both gnome and kde but I prefer the gnome boot screen. How do i change it back? Or better yet, how do i edit my boot screen to make my own?

---

### Post by psyguy92 on 2005-11-23
Funny. Mine just did the same thing a few minutes ago.  My linuxant modem driver didn't want to function under the 686 kernel either, so I rebooted.  I'm going to look for info on this.

Anyone know the answer to the mysterious kubuntu screen?

---

### Post by durand on 2005-11-23
I thought that all i had to do was install the gnome version of the ubuntu kernel but i couldn't find one...

---

### Post by yesplease on 2005-11-23
For kernel upgrades [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

Did you take notes of what you installed? That would make it easier to uninstall it.

---

### Post by seldenthuis on 2005-11-23
[QUOTE=durand]I thought that all i had to do was install the gnome version of the ubuntu kernel but i couldn't find one...[/QUOTE]
There's no such thing as a gnome (or kde) version of the kernel. The kernel has nothing to do with your desktop.

You might wanna try the following, it reconfigures usplash:
```

sudo dpkg-reconfigure usplash
sudo dpkg-reconfigure linux-image-`uname -r`

```

---

### Post by durand on 2005-11-28
tried that but it just changed the grub config... no other difference.

---

