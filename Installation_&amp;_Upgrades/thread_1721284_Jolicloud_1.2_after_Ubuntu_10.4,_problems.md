---
title: "Jolicloud 1.2 after Ubuntu 10.4, problems"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by Sabonmu on 2011-04-04
I use an AO 751h with the dreaded Poulsbo chipset. I have been using Ubuntu 10.4, mainly for office work in a Windows domain, and it's rock solid, even after the mods for the GMA 500.
In a small 14 Gb partition I installed Jolicloud 1.2, clean install, ext 4.
I never got wireless working in Ubuntu 10.4, and I like having a second O/S to 'play with'.
However now after the install, I need to press esc to get the boot menu and Ubuntu (obviously) is not default boot any more.
How can I edit Grub in Jolicloud to get the Grub boot screen back on boot, and to make Ubuntu 10.4 default again?
Can I use Gpart to make the Ubuntu partition 'boot', or am I being naive?
I have a feeling I will need to edit Grub2 in Jolicloud?

---

### Post by mikewhatever on 2011-04-07
The easiest way to achieve both goals is to boot into your 10.04 installation and run the following:
```
sudo grub-install /dev/sda
```

It should make 10.04 the default boot choice, and since Jolicloud will get detected, the grub menu should show at boot.

---

