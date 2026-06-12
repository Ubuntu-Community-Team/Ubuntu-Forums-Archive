---
title: "Possile to change default fstab option during Ubuntu-7.10/Kubuntu-8.04 installations?"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Jags_FL on 2008-01-19
**This post could be related to an Ubuntu bug filed at**: [http://kubuntuforums.net/forums/index.php?topic=3090572.msg111238#msg111238](http://kubuntuforums.net/forums/index.php?topic=3090572.msg111238#msg111238) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				hi everyone

a Ubuntu and Linux newbie here.

Is it possible to change **default fstab options** at Ubuntu/Kubuntu  installation in such a way that Ubuntu's /etc/fstab AND Ubuntu GRUB > Menu.lst **uses device id=/dev/sda*** [B] instead of UUID=...some string...  ?
[/B]

I've recently successfully installed OpenSUSE 11.0 Alpha 0, Debian 4.0 and Fedora 8 and have noticed that all of those OSes' /etc/fstab and GRUB > Menu.lst uses device id=/dev/sda* not the "UUID"


The reason I like to choose (if possible) "device id=/dev/sda*" option is that if I install any other Linux OS after I install Ubuntu, Ubuntu won't boot up, while that's NOT the case with other Linux OSes I've tried (OpenSUSE, Debian & Fedora). [ Details about the "Error 11: Unrecognized devive id" is here:  >>    [http://kubuntuforums.net/forums/index.php?topic=3090572.msg111238#msg111238](http://kubuntuforums.net/forums/index.php?topic=3090572.msg111238#msg111238) ]


I'm not sure about Debian 4.0 / Fedora 8 (can't remember exactly) BUT OpenSUSE 11.0 Alpha 0 does gives you various fstab options before starting installation.



Thanks a million in advance, any help is highly appreciated.

- Jags

---

### Post by logos34 on 2008-01-19
> **Jags_FL said:**
> **Is it possible to change [B]default fstab options** at Ubuntu/Kubuntu  installation in such a way that Ubuntu's /etc/fstab AND Ubuntu GRUB > Menu.lst **uses device id=/dev/sda*** [B] instead of UUID=...some string...  ?
[/B]

You can change it immediately after installation.  Is that ok?

gksudo gedit /boot/grub/menu.lst

Replace the 'root=UUID=...' on the 'kopt' line and 'kernel' lines with 'root=/dev/sda'

Same for fstab.

---

