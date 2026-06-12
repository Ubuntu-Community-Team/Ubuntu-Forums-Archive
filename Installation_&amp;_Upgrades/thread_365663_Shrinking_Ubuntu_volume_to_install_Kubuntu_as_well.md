---
title: "Shrinking Ubuntu volume to install Kubuntu as well"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by Robert A. Morin on 2007-02-19
I am wanting to shrink my Ubuntu Edgy Eft partition with GParted, so I can dual-boot with Kubuntu Dapper on the same external hard drive.  However, it seems to me that the only partition that GParted recognizes for the Kubuntu install is the SWAP drive, which is very little.  How do I shrink the main partition in half so I can install Kubuntu successfully using GParted?  It doesn't seem like it wants to shrink the main partition for this installation.

---

### Post by tubasoldier on 2007-02-19
Why would you do that? you can just install kubuntu to co-exist with Ubuntu

```
sudo apt-get install kubuntu-desktop
```

---

### Post by Robert A. Morin on 2007-02-19
Ahh, I never knew you could do that.  Sorry about that, I'll see what that will do with my GRUB bootloader, would that still give me a choice as to whether I go KDE or GNOME right at the beginning?

---

### Post by tubasoldier on 2007-02-19
No, you make the choice at the login screen. Matter of fact you dont even need to reboot. When you get to GDM just click on menu--> sessions, and you can pick KDE.
If it has not shown up in GDM after you install it then restart your x-server
```
ctl-alt-backspace
```

---

