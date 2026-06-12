---
title: "Ubuntu USB not booting on chromebook"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by remn on 2016-02-25
I'm trying to install Ubunto on a HP Chromebook 14, using the instructions from the Arch wiki for installing linux on chromebooks:

[https://wiki.archlinux.org/index.php/Chrome_OS_devices](https://wiki.archlinux.org/index.php/Chrome_OS_devices)

I was able to enter dev mode and get root access. I think I was also able to enable SeaBIOS because I didn't get an error message when I ran the command from the wiki:

```
# crossystem dev_boot_usb=1 dev_boot_legacy=1
```

However, when I try the next step of rebooting and typing ```
Ctrl + L
``` at the white splash screen, it just beeps without rebooting, then loads Chrome OS. I've tried the same thing with a couple other linux distros on USB drives, and none of them will boot. I tried my Ubuntu usb on another computer and it booted fine. Any way to get my chromebook to boot into Ubuntu, so I can install it on the Chromebook? I don't want to use Crouton becaue I want to entirely remove Chrome OS.

---

### Post by remn on 2016-02-26
Anybody out there have any success installing Ubuntu on a Chromebook? I'm still not having any luck with the HP 14, any other ones that are known to work?

---

