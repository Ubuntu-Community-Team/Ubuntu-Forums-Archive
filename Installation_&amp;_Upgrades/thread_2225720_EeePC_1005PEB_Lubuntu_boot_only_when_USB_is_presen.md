---
title: "EeePC 1005PEB Lubuntu boot only when USB is present"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by Pocc on 2014-05-22
Title says most of it. I installed the Lubuntu minimal install with a USB stick, and then used the command line to "sudo apt-get install lubuntu-desktop". If I don't start with USB selected as the default boot option in the BIOS or remove the USB stick, the computer hangs after POST on a blinking underscore a couple lines from the top. Otherwise it boots just fine. Additionally, the USB stick is not booted, because it goes to its own installation menu.What can I do to ensure that the hard drive boots into the OS without the USB stick?

---

### Post by sudodus on 2014-05-23
I think that you installed the bootloader to the wrong drive. You have two options.

1. Repair the system

Try according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

In order for this to be correct, be sure to identify which device is the internal drive and which device in the USB drive. The output of the following commands should help

```
sudo parted -l
```

```
df
```


2. Install again, this time installing the bootloader to the right drive, the internal one.

---

### Post by Pocc on 2014-05-23
Thank You It Worked! [br]1[/br][br]1[/br]/dev/sda was my internal hard drive, so ```
sudo grub-install /dev/sda 
``` fixed it in one line of code.

---

### Post by sudodus on 2014-05-23
Congratulations :KS

---

