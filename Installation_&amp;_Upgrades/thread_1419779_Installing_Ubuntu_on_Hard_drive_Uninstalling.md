---
title: "Installing Ubuntu on Hard drive Uninstalling"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by nadarm on 2010-03-02
[SIZE=3][FONT=Arial]I have installed Ubuntu 9.04 on Suns Virtual Box.  If I decide to install this OS on my hard drive, does it play nice with Vista?  Would I be able to boot either in Vista and Ubuntu?

The next question is if I decide I want to remove Ubuntu from my laptop, can that be done without wiping out my hard drive?  If anyone has any experience removing this from their system, I would like to hear from on this topic.  Were there any issues removing it from the hard drive? etc
[/FONT][/SIZE]

---

### Post by darkod on 2010-03-02
Yes, it plays nicely with Vista and you will be able to select either vista or ubuntu in grub boot menu.

If you decide to remove it you just delete the ubuntu partitions and restore windows bootloader to the MBR of the hdd. Thee is no need to wipe the whole hdd.

---

### Post by zeroseven0183 on 2010-03-02
You also have the option to install it inside Windows Vista. And if you decide to uninstall it, you can remove it like any other programs in Windows (Add/Remove Programs).

---

### Post by darkod on 2010-03-02
> **zeroseven0183 said:**
> You also have the option to install it inside Windows Vista. And if you decide to uninstall it, you can remove it like any other programs in Windows (Add/Remove Programs).

However, that was never meant to be a long term install for everyday use. And that has been confirmed even by the developed who worked on it.
Wubi is only a way to quickly and without any repartitioning try ubuntu. You have already tried it in VB.
The choice is yours but much more issues can come up with wubi if you use it as long term install, than with ubuntu.

---

### Post by nadarm on 2010-03-02
[SIZE=3]How do you go about restoring the windows MBR should I want to remove Ubuntu from my laptop?[/SIZE]

---

### Post by darkod on 2010-03-02
> **nadarm said:**
> [SIZE=3]How do you go about restoring the windows MBR should I want to remove Ubuntu from my laptop?[/SIZE]

You just use your windows install cd/dvd. If you don't have one you can download vista or 7 repair cd image. It will allow to restore the bootloader but it can't fully install windows (that's why it's free and legal to download).

There are ways to do it even with ubuntu tools from ubuntu live desktop which you can always boot from the cd.

---

### Post by nadarm on 2010-03-05
How do you install Ubuntu inside Vista?  By using VNC or VirtualBox?

---

