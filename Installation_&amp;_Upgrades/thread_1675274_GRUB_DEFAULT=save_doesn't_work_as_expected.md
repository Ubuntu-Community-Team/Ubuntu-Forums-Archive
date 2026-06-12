---
title: "GRUB_DEFAULT=save doesn't work as expected"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by magowiz82 on 2011-01-25
I followed this guide to create a button that makes mine pc reboot in windows:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1490650](http://www.uluga.ubuntuforums.org/showthread.php?t=1490650)

the problem is that when I reboot from windows it keeps windows as mine default instead of setting it to linux (like I wanted) , in another pc this work as I expect but here no.
The configuration is the same:
in /etc/default/grub
```
GRUB_DEFAULT=saved

```
the script that reboots mine pc is :
```
#!/bin/bash
grub-reboot "Windows NT/2000/XP (loader) (on /dev/sda1)"
reboot

```

What should I do?

What I want is that, when clicked, the button reboot in windows once and on next reboot the default is linux, is it possible ?

---

### Post by magowiz82 on 2011-01-25
Now it works as I expect: I rechecked mine script and added the full path to commands, I also enabled the sticky bit to reboot and grub-setenv (perhaps I forgot to do so before)

---

