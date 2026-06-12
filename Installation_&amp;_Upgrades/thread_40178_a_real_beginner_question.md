---
title: "a real beginner question"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by vax on 2005-06-08
I have an AMD 3200 64 PC with MSI mother board
Live CD ubuntu worked perfect
the installation went OK ( I think) but when I started the computer it ended with DOS screen
How do I activate the GNOME?
Hoe do I go back to root

---

### Post by djg on 2005-06-08
[QUOTE=vax]I have an AMD 3200 64 PC with MSI mother board
Live CD ubuntu worked perfect
the installation went OK ( I think) but when I started the computer it ended with DOS screen
How do I activate the GNOME?
Hoe do I go back to root[/QUOTE]
 Typing "sudo /etc/init.d/gdm start" should start the Gnome login screen.

To go back to root, type "cd /".

---

### Post by ZeroA4 on 2005-06-08
There is no DOS. There is no spoon either.

The install must have misconfigured you X (the graphical enviroment upon which the Gnome runs).

What is you video card ? do you know it's chipset ?
Please post your "/etc/X11/xorg.conf" and your "/var/log/Xorg.0.log" and the result of "lspci" please use CODE tags around them.

As you can't start the grafical interface you may have to copy those files to a mounted FAT32 partition or a diskette.

The result of lspci can be saved to a file with "lspci > name.txt"

You can run commands as root by "sudo command". "sudo" will prompt for "Password:". Please specify your user password.

---

### Post by Joeb on 2005-06-08
[QUOTE=ZeroA4]There is no DOS. There is no spoon either.

The install must have misconfigured you X (the graphical enviroment upon which the Gnome runs).

What is you video card ? do you know it's chipset ?
Please post your "/etc/X11/xorg.conf" and your "/var/log/Xorg.0.log" and the result of "lspci" please use CODE tags around them.

As you can't start the grafical interface you may have to copy those files to a mounted FAT32 partition or a diskette.

[/QUOTE]

If it is an X configuration problem, he could probably boot of the live cd, since it works, and copy that configuration file to his install.

---

### Post by ZeroA4 on 2005-06-08
[QUOTE=Joeb]If it is an X configuration problem, he could probably boot of the live cd, since it works, and copy that configuration file to his install.[/QUOTE]Err... yeah that should be even easier.

---

### Post by az on 2005-06-08
Okay, before you do anything, check to see that the install went ok.  It may have failed silently...


log in and type

sudo apt-get -f install


If that does not do anything for you, try

sudo apt-get install ubuntu-desktop.

If everything is already installed, you need to reconfigure your graphics card and monitor with the
sudo dpkg-reconfigure xserver-xorg
command.

Good luck.  Post further questions as needed...

---

