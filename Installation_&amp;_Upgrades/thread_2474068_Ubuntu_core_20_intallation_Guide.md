---
title: "Ubuntu core 20 intallation Guide"
date: 2022-04-21
forum: Installation &amp; Upgrades
---

### Post by duxnor on 2022-04-21
[COLOR=#030303][FONT=Roboto]Hello can you help me please !
[/FONT][/COLOR][COLOR=#030303][FONT=Roboto]1- I installed a new clean Ubuntu core and did not know what the password is ? for user and root ![/FONT][/COLOR][COLOR=#030303][FONT=Roboto](I don't even know how to change the password)
[/FONT][/COLOR][COLOR=#030303][FONT=Roboto]2- how to use file editor [COLOR=inherit][FONT=&amp]nano-strict without this error [/FONT][/COLOR][ Error reading /etc/ssh/sshd_config: Permission denied ]

[/FONT][/COLOR][COLOR=#030303][FONT=Roboto]I have a ssh privet key to connect in Ubuntu Core.[/FONT][/COLOR]

---

### Post by lulosj on 2022-04-21
[https://forum.snapcraft.io/t/how-do-i-provide-a-user-root-privileges-in-ubuntu-core-16/18304](https://forum.snapcraft.io/t/how-do-i-provide-a-user-root-privileges-in-ubuntu-core-16/18304)

---

### Post by duxnor on 2022-04-22
> **lulosj said:**
> [https://forum.snapcraft.io/t/how-do-i-provide-a-user-root-privileges-in-ubuntu-core-16/18304](https://forum.snapcraft.io/t/how-do-i-provide-a-user-root-privileges-in-ubuntu-core-16/18304)

not resolve solution

---

### Post by grahammechanical on 2022-04-22
Please explain your hardware setup. Ubuntu Core is designed to install on an Internet of Things device and then be accessed using SSH (Secure SHell protocol) from another machine running Ubuntu.

I once wanted to experiment with Ubuntu Core but I only had a desktop machine with two hard drives. I installed Ubuntu Core on one hard drive and it booted fine but I could not enter a password or do anything with it because I could not ssh into Ubuntu Core from my installation of Ubuntu on the other drive. It was not loaded. We can only run one OS at a time even if we have more than one OS installed on the hardware.

Please confirm that this install of Ubuntu Core is on a machine that is networked to another machine that runs Ubuntu.

Regards

---

