---
title: "Login problem after upgrading to Kubuntu 10.04.1"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by sandro54 on 2010-12-08
Hi Guys,
I have a problem after upgrading from Kubuntu 9.10 to 10.04.1 (LTS): after reboot I get the login panel but when I type login + password, the system begin to go ahead but immediately comes back to login panel, so I can't get the Desktop obviously .

I checked the following :
The kubuntu-desktop is already in place the kdm I think it works well (start & stop work) and the file xorg.conf has been rebuilded with the cmd "dpkg-reconfigure.......xserver-xorg".

please do you have any idea about the problem ?

thanks in advance.

Sandro

---

### Post by sikander3786 on 2010-12-08
Make sure you are not running out of disk space on any of your partitions.

Press Ctrl + Alt + F1 at the login screen. Login using your credentials and,

```
df -h
```

```
sudo dpkg --configure -a
```

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo shutdown -r now
```

Post any errors encountered. If not successful, post the output of this one as well.

```
lspci | grep VGA
```

---

### Post by Rizwanm on 2010-12-08
Hey really good information guys ....... i dont have that prob then too it helped me thank u so much i am glad i got good information :o:D:)

---

