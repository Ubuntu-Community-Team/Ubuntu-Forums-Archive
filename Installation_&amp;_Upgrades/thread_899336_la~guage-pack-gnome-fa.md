---
title: "la~guage-pack-gnome-fa"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Nossie on 2008-08-24
```
ian@Jupiter-Ubuntu:~$ sudo dpkg --configure -a
[sudo] password for ian: 
dpkg: parse error, in file `/var/lib/dpkg/available' near line 26613 package `language-pack-fa':
 `Replaces' field, invalid package name `la~guage-pack-gnome-fa': character `~' not allowed (only letters, digits and characters `-+._')
ian@Jupiter-Ubuntu:~$ 
```

anyone know how I could fix that? :-|

---

### Post by sisco311 on 2008-08-24
```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo dpkg --configure -a
```

---

### Post by Nossie on 2008-08-24
```


ian@Jupiter-Ubuntu:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
ian@Jupiter-Ubuntu:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-21-generic (2.6.24-21.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules
ian@Jupiter-Ubuntu:~$ 

```

ewww messy  and then 

```

ian@Jupiter-Ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-do-plugins
The following packages will be upgraded:
  avant-window-navigator-data-trunk avant-window-navigator-trunk
  awn-extras-applets-trunk awn-manager-trunk eject gnome-do libawn-doc-trunk
  libawn0-trunk libwebkit-1.0-1 linux-ubuntu-modules-2.6.24-21-generic
  pciutils python-awn-trunk vala-awn-trunk wine wine-dev
15 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
Need to get 0B/22.1MB of archives.
After this operation, 1573kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  python-awn-trunk libawn0-trunk avant-window-navigator-trunk
  avant-window-navigator-data-trunk libwebkit-1.0-1 awn-extras-applets-trunk
  awn-manager-trunk gnome-do libawn-doc-trunk vala-awn-trunk
Install these packages without verification [y/N]? y
(Reading database ... 256634 files and directories currently installed.)
Preparing to replace linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.30 (using .../linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.31_i386.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.24-21-generic ...
Preparing to replace wine-dev 1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1 (using .../wine-dev_1.1.3~winehq0~ubuntu~8.04-0ubuntu1_i386.deb) ...
Unpacking replacement wine-dev ...
Preparing to replace wine 1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1 (using .../wine_1.1.3~winehq0~ubuntu~8.04-0ubuntu1_i386.deb) ...
Unpacking replacement wine ...
Preparing to replace eject 2.1.5-6 (using .../eject_2.1.5-6ubuntu1_i386.deb) ...
Unpacking replacement eject ...
Preparing to replace pciutils 1:2.2.4-1.1ubuntu5 (using .../pciutils_1%3a2.2.4-1.1ubuntu6_i386.deb) ...
Unpacking replacement pciutils ...
Preparing to replace python-awn-trunk 0.3.1~bzr467-hardy1-1 (using .../python-awn-trunk_0.3.1~bzr475-hardy1-1_i386.deb) ...
Unpacking replacement python-awn-trunk ...
Preparing to replace libawn0-trunk 0.3.1~bzr467-hardy1-1 (using .../libawn0-trunk_0.3.1~bzr475-hardy1-1_i386.deb) ...
Unpacking replacement libawn0-trunk ...
Preparing to replace avant-window-navigator-trunk 0.3.1~bzr467-hardy1-1 (using .../avant-window-navigator-trunk_0.3.1~bzr475-hardy1-1_i386.deb) ...
Unpacking replacement avant-window-navigator-trunk ...
Preparing to replace avant-window-navigator-data-trunk 0.3.1~bzr467-hardy1-1 (using .../avant-window-navigator-data-trunk_0.3.1~bzr475-hardy1-1_all.deb) ...
Unpacking replacement avant-window-navigator-data-trunk ...
Preparing to replace libwebkit-1.0-1 0~svn32442-1~ppa1.1 (using .../libwebkit-1.0-1_1.0.1-2~ppa1_i386.deb) ...
Unpacking replacement libwebkit-1.0-1 ...
Preparing to replace awn-extras-applets-trunk 0.3.1~bzr836-hardy1-1 (using .../awn-extras-applets-trunk_0.3.1~bzr847-hardy1-1_i386.deb) ...
Unpacking replacement awn-extras-applets-trunk ...
Preparing to replace awn-manager-trunk 0.3.1~bzr467-hardy1-1 (using .../awn-manager-trunk_0.3.1~bzr475-hardy1-1_all.deb) ...
Unpacking replacement awn-manager-trunk ...
Preparing to replace gnome-do 0.5.99.0-0~hardy~ppa1 (using .../gnome-do_0.6.0.0-0~hardy~ppa1_i386.deb) ...
Unpacking replacement gnome-do ...
Preparing to replace libawn-doc-trunk 0.3.1~bzr467-hardy1-1 (using .../libawn-doc-trunk_0.3.1~bzr475-hardy1-1_all.deb) ...
Unpacking replacement libawn-doc-trunk ...
Preparing to replace vala-awn-trunk 0.3.1~bzr467-hardy1-1 (using .../vala-awn-trunk_0.3.1~bzr475-hardy1-1_all.deb) ...
Unpacking replacement vala-awn-trunk ...
Setting up linux-image-2.6.24-21-generic (2.6.24-21.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Setting up wine (1.1.3~winehq0~ubuntu~8.04-0ubuntu1) ...

Setting up wine-dev (1.1.3~winehq0~ubuntu~8.04-0ubuntu1) ...
Setting up eject (2.1.5-6ubuntu1) ...
Setting up pciutils (1:2.2.4-1.1ubuntu6) ...

Setting up libawn0-trunk (0.3.1~bzr475-hardy1-1) ...

Setting up python-awn-trunk (0.3.1~bzr475-hardy1-1) ...

Setting up libwebkit-1.0-1 (1.0.1-2~ppa1) ...

Setting up awn-extras-applets-trunk (0.3.1~bzr847-hardy1-1) ...

Setting up gnome-do (0.6.0.0-0~hardy~ppa1) ...
Setting up libawn-doc-trunk (0.3.1~bzr475-hardy1-1) ...

Setting up vala-awn-trunk (0.3.1~bzr475-hardy1-1) ...
Setting up avant-window-navigator-data-trunk (0.3.1~bzr475-hardy1-1) ...

Setting up avant-window-navigator-trunk (0.3.1~bzr475-hardy1-1) ...

Setting up awn-manager-trunk (0.3.1~bzr475-hardy1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ 


```


Any help is greatly appreciated ! :) thanks for your time Sisco

---

### Post by Nossie on 2008-08-25
Hi,

I seemed to be able to fix most of the previous errors by removing the remains of the latest kernel .. but when I try adding it back in it says some dependencies are not met... any thoughts?

cheers,
Ian.


```

ian@Jupiter-Ubuntu:~$ sudo apt-get upgrade
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-do-plugins
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
ian@Jupiter-Ubuntu:~$ sudo apt-get upgrade
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-do-plugins
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-21-generic (2.6.24-21.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ 

```

---

