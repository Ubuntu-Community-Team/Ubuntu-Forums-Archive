---
title: "Error 15: grub4dos file not found"
date: 2019-03-18
forum: Installation &amp; Upgrades
---

### Post by anirna on 2019-03-18
For some reason the existing operating system(Fedora is giving kernel  panic error) so i decided to install Ubuntu 16.04.5 LTS desktop version.  When i boot using bootable USB it just shows 2 options: (no "Try ubuntu without installing" option)

[LIST]
[*]Ubuntu without acpi off
[*]Ubuntu with acpi off
[*]The main problem which i'm facing is the error: "Error 15: grub4dos file not found".
[/LIST]
Thanks.

---

### Post by yancek on 2019-03-18
What happens when you select either/both options on acpi on or off?  I don't know why an Ubuntu installer would be looking for grub4dos as that is windows software?

---

### Post by oldfred on 2019-03-18
Did you install wubi, which is not supported anymore as it uses grub4dos.
Or are you using EasyBCD which uses the now very old grub4dos.
Or do you have a DVD or flash drive with multiple installs that uses grub4dos.

The grub4dos is based on grub now grub legacy, and Ubuntu has used grub2 since 2009 or last 10 years.

       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by anirna on 2019-03-20
When i select either of the two, it gives out the error which i mentioned in 3rd bullet.

---

### Post by anirna on 2019-03-20
I was trying to boot in legacy mode. I changed the mode to UEFI and set  the proper boot option in BIOS and rebooted the computer. Thanks @oldfred and @yancek, your posts helped me.

---

