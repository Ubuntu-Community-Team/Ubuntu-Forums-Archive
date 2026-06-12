---
title: "Likewise open install with preseed not working"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by chrisdee on 2011-01-06
Hello.

I'm having trouble installing likewise open through preseed.
I'v used the example from [https://help.ubuntu.com/10.04/installation-guide/example-preseed.txt](https://help.ubuntu.com/10.04/installation-guide/example-preseed.txt) as the source of my preseed file.

It works just fine installing openssh, smbfs and libpam-mount. Se the code below. But if I try adding likewise to the code below installation stops when the likewise package is starting to install.

Any suggestions ?

> 
# Individual additional packages to install
d-i pkgsel/include string openssh-server build-essential smbfs libpam-mount
# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
#d-i pkgsel/upgrade select none


---

### Post by chrisdee on 2011-01-10
Also having trouble with the keyboard layout. I'm trying to preseed install english lucid, but with norwegian keyboard layout. Seems like either > d-i debian-installer/locale string en_US or > d-i debian-installer/locale string nb_NO string in the preseed file is ignored.

I have to define the install language in the > ubuntu-installer-lucid\i386\boot-screens\text.cfg file. But I don't know how or if it's possible to also define keyboard layout in this file aswell ?

---

### Post by jfluhmann on 2012-02-28
Came across this post while I was searching for something else.  I realize it's over a year old now, but just wanted to put this out there, just in case.

Here's what my preseed "locale" looks like
```
d-i     debian-installer/locale string en_US.UTF-8

```

To get Likewise-open to install properly, you need to pass the 'install' parameter to it for a silent install.  What I did was put it into a post_install.sh script and call that script from within my preseed.

Here's what I have at the end of my preseed file
```
d-i     preseed/late_command string wget http://example.com/additions.tar.gz -P /target/root/; chroot /target tar xvzf /root/additions.tar.gz -C /root/;chroot /target chmod +x /root/additions/post_install.sh; chroot /target bash /root/additions/post_install.sh

```

The additons.tar.gz contains my post_install.sh script, as well as the Likewise package that I'm installing.

And inside the additions/post_install.sh file
```
# package downloads available from
#    http://www.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services/
LIKEWISE_PKG=/root/additions/LikewiseOpen-6.0.0.8388-linux-amd64-deb.sh
chmod +x $LIKEWISE_PKG
$LIKEWISE_PKG install

```

---

