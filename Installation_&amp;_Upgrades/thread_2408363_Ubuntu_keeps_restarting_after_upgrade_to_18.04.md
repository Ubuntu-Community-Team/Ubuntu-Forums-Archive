---
title: "Ubuntu keeps restarting after upgrade to 18.04"
date: 2018-12-17
forum: Installation &amp; Upgrades
---

### Post by ntarunmenon on 2018-12-17
I updated ubuntu from 18.04 from 16.04. On start I get grub as expected with 2 options

1. Windows boot manager.
2. grubx64efi

. I choose 'grubx64efi option expecting to get into ubuntu, but the system reboots and then lands back in grub.

I have tried starting up from USB and running boot repair. Didnt help and I keep getting the same problem. The boot-repair seems to have run without any errors.

While I doing the update I was asked something along the lines of what to d with your grub and I chose an option which says to keep the configuration as is now. Could this be causing an issue ? How do I resolve this ?

I have Acer Aspire E15 with dual boot with windows 10. I was using 16.04 without any issues previously.

---

### Post by QIII on 2018-12-17
Hello!

How did you initially install Ubuntu?

---

### Post by ntarunmenon on 2018-12-17
The 16.x version was installed by creating a bootable usb image. I upgraded to 18.04 from within the upgrade option in Ubuntu 16.x.

Thanks for the reply

---

### Post by QIII on 2018-12-17
Did you, by chance, use WUBI to install Ubuntu?

What you have described looks like what one would expect the Windows boot loader to present after a WUBI install.

Could you get a shot of that screen using a phone camera?

Upgrading Ubuntu in a dual boot with Windows also sometimes causes strange things.

---

### Post by ntarunmenon on 2018-12-17
Attached a screenshot. I think my grub config has been corrupted for some reason(Captain Obvious here).

---

### Post by QIII on 2018-12-17
I would expect a proper GRUB menu to look somewhat like this:

[ATTACH=CONFIG]281957[/ATTACH]

Have you ever seen it like that?

What you have there appears to be the Windows bootloader menu.

---

### Post by ntarunmenon on 2018-12-17
I dont remember ever seeing an advanced option for ubuntu in my menu. So I am pretty sure I did not have the menu that you have attached in 16.04.

Do you have any pointers where I can start solving this. 

So far the only thing I have is [I]"[COLOR=#242729][FONT=Arial]grubx64.efi refers to GRUB file only. Menu entry for Ubuntu is missing in your grub. I believe[/FONT][/COLOR]" from [here]("https://askubuntu.com/questions/1102653/ubuntu-keeps-restarting-after-upgrade-to-18-04?noredirect=1#comment1817219_1102653").


[/I]

---

### Post by QIII on 2018-12-17
The first diagnostic question I asked is whether you installed Ubuntu with WUBI.  That is, were you running Windows and did you install Ubuntu from Windows?

If not, there may be something else to look at.

---

### Post by ntarunmenon on 2018-12-17
I did not run WUBI to install Ubuntu. The 16.x version was installed by creating a bootable usb image and installing from the boot options.

---

### Post by ntarunmenon on 2018-12-18
I solved the issue by running boot-repair again. I am able to access ubuntu now. Thanks for your help.

---

