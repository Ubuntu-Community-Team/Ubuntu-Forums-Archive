---
title: "Problems booting Ubuntu 19.04 on Acer Nitro AN515-42"
date: 2019-10-16
forum: Installation &amp; Upgrades
---

### Post by johnplshelp123 on 2019-10-16
Hello, I've tried installing Ubuntu on my laptop but it has a couple of peculiar problems.
Firstly, it boots fine when I add the noapic or acpi=off commands at grub boot (unfortunately this disables the trackpad), but by experimentation I have discovered that there is another weird way to get it to boot: by closing and opening the laptop lid at some point during the boot process makes it boot up just fine, trackpad working and all.
Now my question is, is there any way for me to boot normally without manically closing and opening my laptop lid while booting?

---

### Post by #&amp;thj^% on 2019-10-16
Look Here with the post from oldfred, Starts:
"It looks like Acer Nitro need **"pci=noacpi"** boot parameter. Many systems need one or several boot parameters. If nVidia nomodeset parameter required."
Post found here with GPU options: [https://askubuntu.com/questions/1146297/unable-to-boot-from-usb-sdd-on-acer-nitro-5-an-515-42-with-radeon-rx560](https://askubuntu.com/questions/1146297/unable-to-boot-from-usb-sdd-on-acer-nitro-5-an-515-42-with-radeon-rx560)

---

### Post by oldfred on 2019-10-16
Have you updated UEFI from Acer?
You may have to reset some of the settings you changed in UEFI as it reverts to defaults on update.

Not your specific issue, but maybe related:
[SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by johnplshelp123 on 2019-10-16
Yeah, yeah, I've read through all of those, my question is why then does it boot up when I do something as inane as closing and opening my laptop lid? and if there's any way to replicate that so everything works fine without using noacpi

---

### Post by #&amp;thj^% on 2019-10-16
Sounds like a question for Acer or a Developer none of which hang out here.
Forum posting tip: Tone of voice is so easily misinterpreted online. Go out of your way to be gracious and appreciative.

---

