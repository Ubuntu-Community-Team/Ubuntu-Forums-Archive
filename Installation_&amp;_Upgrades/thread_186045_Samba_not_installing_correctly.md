---
title: "Samba not installing correctly"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by HJB on 2006-06-01
Hi, I did an upgrade and also switched from Gnome to Xfce. Everything went fine but the following shows up everytime I install something now:
> Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

What is this, where should I look for info, and how do I fix this?

Every thing was fine a couple of nights ago.
Bye
H

---

### Post by digby280 on 2006-06-03
It's a bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/9208](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/9208)

I found a solution that works for me here:
[http://ubuntuforums.org/archive/index.php/t-6318.html](http://ubuntuforums.org/archive/index.php/t-6318.html)

Just:
sudo ln -s /etc/init.d/samba /etc/rc2.d/samba
sudo ln -s /etc/init.d/samba /etc/rc3.d/samba
sudo apt-get -f install

---

### Post by HJB on 2006-06-04
[QUOTE=digby280]It's a bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/9208](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/9208)

I found a solution that works for me here:
[http://ubuntuforums.org/archive/index.php/t-6318.html](http://ubuntuforums.org/archive/index.php/t-6318.html)

Just:
sudo ln -s /etc/init.d/samba /etc/rc2.d/samba
sudo ln -s /etc/init.d/samba /etc/rc3.d/samba
sudo apt-get -f install[/QUOTE]

HI digby280. Thanx it worked. All I had to do extra was delete the two dangling links.

Bye
H

---

