---
title: "Ubuntu boots to CLI"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by jordanae on 2009-12-30
I just got a new computer and decided to install Ubuntu 9.10 64-bit. My computer came with Windows 7 and so I dual booted saving Windows for gaming. In case it helps I installed them side by side so I could just choose them from the GRUB menu. But the problem I'm having is that when I boot up Ubuntu it goes straight into terminal. No GUI at all. I'm sure I downloaded the desktop version and I know that my computer can handle 64-bit. 

I also ran apt-get install ubuntu-desktop to see if I had gnome and everything installed and it says that it is.

---

### Post by staf0048 on 2009-12-30
This might be worth a shot, try starting the gui w/ 

```
sudo /etc/init.d/gdm start
```

Let us know if that does anything...

---

### Post by jordanae on 2009-12-30
I couldn't type anything when I booted it up. The screen was flashing and not every key would work. I think it's just a faulty cd so I'll just install it from a new one. Can I uninstall Ubuntu and keep Windows 7 even though I did a side by side install?

---

### Post by wilee-nilee on 2009-12-30
Of you have installed side by side removing Linux will leave you needing to update the MBR with the W7 install disc in order to access W7. You might just see if you can load Ubuntu onto a thumb or burn a new CD if you want both OS in the end.

---

