---
title: "Uninstalling Gnome-Keyring Killed Vital Packages"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by stwstl5926 on 2010-03-22
I got my room-mate to switch to Ubuntu a while back, and he loves it, but he hated the Keyring. So, logically, he tried uninstalling the Keyring package (gnome-keyring). Of course, this also uninstalled some other vital packages. According to my Ubuntu box, this is what would be uninstalled from my system if I did what he did (forgive me if there are unrelated packages in there):

[LIST]
[*]apturl
[*]checkbox-gtk
[*]gdebi
[*]gksu
[*]gnome-codec-install
[*]network-manager-gnome
[*]software-properties-gtk
[*]ubufox
[*]update-manager
[*]update-notifier
[/LIST]
As you may have noticed, he killed his network manager, which means he now has no internet to reinstall the missing packages. He also killed gdebi, which means I can't just install the network manager via a stand-alone .deb package.

Ideas?

---

### Post by 2hot6ft2 on 2010-03-22
I'm not even sure you can do this without the Gnome-Keyring but here goes.

If you have a wired connection you could setup a basic connection like this
Open a terminal
Applications > Accessories > Terminal
and run
I see gksu was removed so have to try sudo or maybe without the sudo part at all
```
sudo gedit /etc/network/interfaces
```
Put this in it, the first part should already be there so just add the second part which is in bold
> auto lo
iface lo inet loopback

[B]auto eth0
iface eth0 inet dhcp[/B]
Save and close it.
Reboot

While you wont have a network manager applet to show you it's connected it should connect.
Try going somewhere or running ```
sudo apt-get update
```
Good luck

Once you have network manager and the network manager applet back edit the file again and remove those 2 lines but be sure NOT to remove the first 2 lines.

---

### Post by stwstl5926 on 2010-03-22
That did the trick. Thanks!

---

