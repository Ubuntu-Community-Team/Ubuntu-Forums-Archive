---
title: "No graphical boot or X after edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by hambone79 on 2006-10-27
I upgrade to edgy this morning via apt-get and now there seems to be a serious problem. It appears that all the packages updates without a problem (it should since I was using  a pretty basic install), but now I cannot start X. I keep getting an "xinit: Connection refused (errno 111): unable to connec to X server" whenever I try to start X. Also, I no longer have the nice Ubuntu graphic boot screen. Does anyone have any idea how to fix this? I really need my laptop!

---

### Post by filogo on 2006-10-27
You just have to reinstall xorg

```
sudo apt-get install xorg
```

if it asks for dependencies install asked packages.

---

### Post by hambone79 on 2006-10-27
Ok, that fixed X. Now what do I need to install/reinstall to fix the graphical boot screen?

---

### Post by barmaley on 2006-10-29
Hello, people

I think I have similar problem, except xorg works fine after the upgrade.
I don't see the boot screen and I don't see the shutdown screen. The monitor writes a typical message "Signal out of range ... Mode should be below 1280x1024 75Hz".
Does anyone knows how to fix this problem or at least switch back to text mode boot and shutdown.

Thank you in advance

---

### Post by percival95 on 2006-11-06
I have a similar problem but I only get a blank screen. How do you fix that? Download the cd?

---

