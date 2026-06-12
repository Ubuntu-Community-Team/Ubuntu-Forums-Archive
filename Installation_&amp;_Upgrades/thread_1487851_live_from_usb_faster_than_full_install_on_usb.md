---
title: "live from usb faster than full install on usb"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by jeffjanzen on 2010-05-19
I have 2 _USB flash drives_ with ubuntu lucid amd64:

[LIST]
[*]1 **live boot **(persistent) created with iso and Universal-USB-Installer-v1.5.5.exe (from pendrivelinux.com)
[*]1 **normal **installation where I simply selected my flash drive instead of my hard drive.
[/LIST]

When running the normal installation, I encounter frequent delays during normal operations. For example, I'll open synaptic package manager, and I'll just have to wait there almost 15 seconds for it to load. Sometimes, I'll click on the applications menu and just sit there a few seconds before it drops down. And while I'm using Firefox, it often hangs (indicated by turning grayscale colors) for a few seconds before loading a page or before opening up the "Add-ons" window.

With live boot, I have *none of these delays*. Can anyone explain to me WHY and/or how to make my normal installation run as fast as the live boot?

Thanks.

Note: Both are installed on SanDisk cruzer micros. Live boot from 1gb drive, normal install on 8gb drive. Also, I have added the following line to fstab so I'm using tmpfs for /tmp:
```
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0
```

---

### Post by cefn on 2012-07-15
I've been experimenting to improve performance in this case too. I found that setting up certain parts of the filesystem as tmpfs in RAM (those which are accessed often as part of moment-to-moment operation) eliminated the slowdowns and hangs I was experiencing.

You can see a bit more about how this is typically configured, and some paths to try adding to the /etc/fstab file as RAM-mounted directories here...

[https://wiki.archlinux.org/index.php/Fstab#tmpfs](https://wiki.archlinux.org/index.php/Fstab#tmpfs)

...but note that the information is lost on a reboot, so it's only applicable to temporary files. 

For my own purposes I have my google-chrome cache (at /home/<username>/.cache/google-chrome) and profile at /home/<username>/.config/google-chrome) also running on tmpfs in a similar way, meaning my browser is very fast where previously it spent all its time reading from cache, and I can use a Chrome sign-in to google to preserve bookmarks etc. between sessions and between machines).

---

