---
title: "Blinking cursor at boot"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by permagnus on 2011-12-09
Hi,

After doing an install from the mini iso (booted from an usb drive) I'm only getting a blinking cursor at boot. The system however seems to be up and running because I can ssh to it and access the system.

Here is the results.txt file from the bootinfo script: [http://dl.dropbox.com/u/63179/results.txt](http://dl.dropbox.com/u/63179/results.txt)

Any ideas?

---

### Post by BC59 on 2011-12-09
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank+screen](http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank+screen)
add nomodeset as kernel parameter in the grub boot menu.

---

### Post by permagnus on 2011-12-09
Changing the grub config line from:
```

linux   /boot/vmlinuz-3.0.0-13-generic root=UUID=52fedee6-1320-439b-b3cc-ab5606df7b3d ro   splash quiet vt.handoff=8

```

to
```

linux   /boot/vmlinuz-3.0.0-13-generic root=UUID=52fedee6-1320-439b-b3cc-ab5606df7b3d ro nomodeset

```

Seems to have done the trick

---

