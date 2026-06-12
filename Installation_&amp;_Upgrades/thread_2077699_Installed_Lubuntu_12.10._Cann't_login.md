---
title: "Installed Lubuntu 12.10. Cann't login?"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by teraset on 2012-10-29
I have a netbook which installed Lubuntu 12.04. I upgrade it to newest version 12.10. When upgrade have finish, and reboot my netbook, starting up not go to Lubuntu. just stuck black screen where askin username and password. So, I have install it again for clean style but same problem: Startup not go to graphite login, only stay balck screen.
This image is not from my netboot, but like same:
 
[IMG]http://people.gnome.org/~bmsmith/build-brigade-vm/resources/vm1.png[/IMG]

---

### Post by BenginM on 2012-10-29
Type your ubuntu user name , and password to login .. then see if you are able to reach the desktop . if not , then you may need to reconfigure X .

---

### Post by dino99 on 2012-10-29
boot on recovery mode (hit "shift" key down at bios end process to get the grub menu) and select root command line

apt-get install -reinstall lightdm  lightdm-gtk-greeter
dpkg-reconfigure lightdm

and then reboot

---

### Post by ajgreeny on 2012-10-29
What happens if you login at that screen using your username and password, then use command "startx"?

---

