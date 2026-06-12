---
title: "Issue with package &quot;linux-image-3.2.0-24-generic-pae&quot;"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by ryghlles on 2012-05-04
Hi there,

I am a Linux newbie and just installed Ubuntu on my Dell D630.  I have had problems when trying to install a number of different programs as there seems to be an issue with "linux-image-3.2.0-24-generic-pae".  For example, when I try to install Chrome I get the following error:

[INDENT]installArchives() failed: Selecting previously unselected package libxss1. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 177827 files and directories currently installed.) 
Unpacking libxss1 (from .../libxss1_1%3a1.2.1-2_i386.deb) ... 
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae 
cryptsetup: WARNING: failed to detect canonical device of overlayfs 
cryptsetup: WARNING: could not determine root device from /etc/fstab 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-24-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-24-generic-pae; however: 
  Package linux-image-3.2.0-24-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-pae: 
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.24.26); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
Setting up libxss1 (1:1.2.1-2) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-3.2.0-24-generic-pae 
 linux-image-generic-pae 
 linux-generic-pae 
Error in function:  
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae 
cryptsetup: WARNING: failed to detect canonical device of overlayfs 
cryptsetup: WARNING: could not determine root device from /etc/fstab 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-24-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-24-generic-pae; however: 

[/INDENT]

---

### Post by ryghlles on 2012-05-04
This is on Ubuntu 12.04, by the way.  Let me know what other info would help debug this, and thanks for looking!

---

### Post by jadtech on 2012-05-04
have you been to update manager at all and updated software at all ?? 

upper far right corner circle looks like a gear click it on the menu click software update then click the check button  and install everything listed, even if the is no notice do a restart..

after that try to install programs like chrome from the software center on the launch bar looks like a over filled shopping bag icon.. thing is your linux (ubuntu) has to be up to date at time before you can install new stuff and once installed the update manager will keep them up to date with all other programs

---

### Post by ryghlles on 2012-05-04
Thanks.  I tried that but I get a "Package operation failed" error.  

It says: The installation or removal of a software package failed.  I am running Linux from a USB thumb drive; I'm not sure if that is related?

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 178481 files and directories currently installed.) 
Preparing to replace flashplugin-installer 11.2.202.233ubuntu2 (using .../flashplugin-installer_11.2.202.235ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement flashplugin-installer ... 
Preparing to replace libqtbamf1 0.2.3-0ubuntu1 (using .../libqtbamf1_0.2.4-0ubuntu1_i386.deb) ... 
Unpacking replacement libqtbamf1 ... 
Preparing to replace python-software-properties 0.82.7 (using .../python-software-properties_0.82.7.1_all.deb) ... 
Unpacking replacement python-software-properties ... 
Preparing to replace software-properties-common 0.82.7 (using .../software-properties-common_0.82.7.1_all.deb) ... 
Unpacking replacement software-properties-common ... 
Preparing to replace software-properties-gtk 0.82.7 (using .../software-properties-gtk_0.82.7.1_all.deb) ... 
Unpacking replacement software-properties-gtk ... 
Preparing to replace thunderbird-globalmenu 11.0.1+build1-0ubuntu2 (using .../thunderbird-globalmenu_12.0.1+build1-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement thunderbird-globalmenu ... 
Preparing to replace thunderbird 11.0.1+build1-0ubuntu2 (using .../thunderbird_12.0.1+build1-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement thunderbird ... 
Preparing to replace thunderbird-gnome-support 11.0.1+build1-0ubuntu2 (using .../thunderbird-gnome-support_12.0.1+build1-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement thunderbird-gnome-support ... 
Processing triggers for update-notifier-common ... 
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz) 
Installing from local file /tmp/tmpXYSOIc.gz 
Flash Plugin installed. 
Processing triggers for man-db ... 
Processing triggers for shared-mime-info ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae 
cryptsetup: WARNING: failed to detect canonical device of overlayfs 
cryptsetup: WARNING: could not determine root device from /etc/fstab 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-24-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-24-generic-pae; however: 
  Package linux-image-3.2.0-24-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-pae: 
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.24.26); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
Setting up flashplugin-installer (1No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
1.2.202.235ubuntu0.12.04.1) ... 
Setting up libqtbamf1 (0.2.4-0ubuntu1) ... 
Setting up python-software-properties (0.82.7.1) ... 
Setting up software-properties-common (0.82.7.1) ... 
Setting up software-properties-gtk (0.82.7.1) ... 
Setting up thunderbird (12.0.1+build1-0ubuntu0.12.04.1) ... 
Installing new version of config file /etc/apport/blacklist.d/thunderbird ... 
Setting up thunderbird-globalmenu (12.0.1+build1-0ubuntu0.12.04.1) ... 
Setting up thunderbird-gnome-support (12.0.1+build1-0ubuntu0.12.04.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-3.2.0-24-generic-pae 
 linux-image-generic-pae 
 linux-generic-pae 
Error in function:  
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae 
cryptsetup: WARNING: failed to detect canonical device of overlayfs 
cryptsetup: WARNING: could not determine root device from /etc/fstab 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-24-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2

---

### Post by jadtech on 2012-05-04
are you saying your just running  from the thumb drive you burned the ISO to ?? 

I dont beleive you can update  or install or update anything running from live USB or CD it ubuntu has to be installed  on a partition  to do that the image only has bare basic kernel and drivers to be able to boot so you can install ..

you can try it that way  you can get online and the fire fox  will start you can use the other programs as they are just to try them basically  it puts things to the test if  you can boot from USB or CD then Ubuntu will  usually run without modifications when its installed.

---

### Post by jcfagny on 2012-05-18
Hello,
I've got the same problem after 3 Precise installations on a USB key.
It's ok at first time but after the first upgrade :

Paramétrage de linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
/usr/sbin/grub-probe : erreur : cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010.
dpkg : erreur de traitement de linux-image-3.2.0-24-generic-pae (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Paramétrage de libgnome-control-center1 (1:3.4.1-0ubuntu2) ...
Traitement des actions différées (« triggers ») pour « libc-bin »...
ldconfig deferred processing now taking place
Des erreurs ont été rencontrées pendant l'exécution :
 linux-image-3.2.0-24-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

==> linux-image-3.2.0-24-generic-pae : may I remove it ? How ? It seems like something hangs somewhere !

---

### Post by jcfagny on 2012-05-18
Hello,
I've got the same problem after 3 Precise installation on a USB key.
It's ok at first time but after the first upgrade :

Paramétrage de linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
/usr/sbin/grub-probe : erreur : cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010.
dpkg : erreur de traitement de linux-image-3.2.0-24-generic-pae (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Paramétrage de libgnome-control-center1 (1:3.4.1-0ubuntu2) ...
Traitement des actions différées (« triggers ») pour « libc-bin »...
ldconfig deferred processing now taking place
Des erreurs ont été rencontrées pendant l'exécution :
 linux-image-3.2.0-24-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

==> linux-image-3.2.0-24-generic-pae : may I remove it ? How ? It seems like something hangs somewhere !

---

### Post by jadtech on 2012-05-18
not sure  what you are trying to do what you are running   or how thereis loads or errors  looking for devices looking unable to find mounted dev 

Try this then go from there

```

sudo apt-get clean

sudo apt-get update 

sudo apt-get install -f
 


``` 

 do you actually have ubuntu installed on a partition some how or are you just using it from boolable USB from image ..

maybe this link can be  some help to you 

[http://ubuntuforums.org/showthread.php?p=11501472](http://ubuntuforums.org/showthread.php?p=11501472)

---

### Post by jcfagny on 2012-05-19
Thanks for your answer.  I use the USB key to run (and try) Precise. I've used the command given in the link (with the italian guy) but nothing changed.
Here is the result of  'sudo dpkg --configure -a' :

Paramétrage de linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
/usr/sbin/grub-probe : erreur : cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010.
dpkg : erreur de traitement de linux-image-3.2.0-24-generic-pae (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
dpkg : des problèmes de dépendances empêchent la configuration de linux-image-generic-pae :
 linux-image-generic-pae dépend de linux-image-3.2.0-24-generic-pae ; cependant :
 Le paquet linux-image-3.2.0-24-generic-pae n'est pas encore configuré.
dpkg : erreur de traitement de linux-image-generic-pae (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de linux-generic-pae :
 linux-generic-pae dépend de linux-image-generic-pae (= 3.2.0.24.26) ; cependant :
 Le paquet linux-image-generic-pae n'est pas encore configuré.
dpkg : erreur de traitement de linux-generic-pae (--configure) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 linux-image-3.2.0-24-generic-pae
 linux-image-generic-pae
 linux-generic-pae

==> some 'dependances'  : linux-generic-pae dépend de linux-image-generic-pae (= 3.2.0.24.26) ; cependant :
 Le paquet linux-image-generic-pae n'est pas encore configuré (is not configured)  !!!!!!

---

