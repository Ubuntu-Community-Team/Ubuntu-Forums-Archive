---
title: "Using PXELINUX to enable deployment of Windows OS + Linux OS distro"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by jackhifi on 2013-02-19
hi, 
First, thanks to take a look at this article !
Kindly thanks to your advice and comment in advance.
------------
Allright, my purpose is => To use PXELINUX to deployment windows OS + Linux OS
i've setup a Desktop with windows 2008 server R2 and can successfully desploy
windows 7 and windows 8 with windows WADK  toolkit. 

The SOP that i use to reference is from this URL:
[COLOR=black][FONT=Arial][http://goo.gl/CZcXO](http://goo.gl/CZcXO)[/FONT][/COLOR][COLOR=black][FONT=Arial] 
[/FONT][/COLOR]
However , i encounter some issue  on some linux distro  :(
here's my status:

Hadware/Software background:
Desktop A
OS:Windows server 2008 R2 with SP1
service:[SIZE=2][COLOR=black][FONT=Arial]WADK+AD DS+DHCP+WDS+MDT 2012+[/FONT][/COLOR][COLOR=blue][FONT=Arial] syslinux package [/FONT][/COLOR][/SIZE]insatlled
ip address: 192.168.100.100

Desktop B
OS:FreeNAS 8.2
service: NFS service enable
ip address:192.168.100.101

Results:
I can successfully install below ubuntu distro.
ubuntu-12.04.1-DVD-i386 
ubuntu-12.04.1-Desktop-i386 
ubuntu-12.10-Desktop-i386 
here's one of the successful demo i put at youtube
=> [U][COLOR=blue][FONT=Arial]
[https://youtu.be/cCcoZTZW1OM](https://youtu.be/cCcoZTZW1OM)[/FONT][/COLOR][/U]  

However, i encounter stop message with below ubuntu distro.
ubuntu-12.04.1-Server-i386 
ubuntu-12.10-Server-i386 
ubuntu-12.10-Server-AMD64 
here's one of the fail demo i put at youtube [U][COLOR=blue][FONT=Arial]
[/FONT][/COLOR][/U]=> [U][COLOR=blue][FONT=Arial]
[/FONT][/COLOR][/U]_[COLOR=blue][FONT=Arial][https://youtu.be/SHpQpijjO1A](https://youtu.be/SHpQpijjO1A)[/FONT][/COLOR]_[U][COLOR=blue][FONT=Arial] 
[/FONT][/COLOR][/U]
i found that the "server edition" of ubuntu distro doesn't have a folder "casper"
i'm not sure what exactly was this folder "casper" for ?

Please kindly help me to install the "server edition" with my current enviroment.

thank you !!

Below is the key configuration file under pxelinux.cfg folder.

-----

MENU TITLE Setup Menu 
LABEL Main Menu 
MENU LABEL ^0----Return to Main Menu 
KERNEL vesamenu.c32 
MENU BACKGROUND wds.jpg 
APPEND pxelinux.cfg/default 


LABEL d 
MENU LABEL ^D----ubuntu-12.04.1-DVD-i386 
kernel linux/5/vmlinuz 
append root=/dev/nfs initrd=linux/5/initrd.lz boot=casper netboot=nfs nfsroot=192.168.100.101:/mnt/asus/5/cd

LABEL e 
MENU LABEL ^E----ubuntu-12.04.1-Desktop-i386 
kernel linux/4/vmlinuz 
append root=/dev/nfs initrd=linux/4/initrd.lz boot=casper netboot=nfs nfsroot=192.168.100.101:/mnt/asus/4

LABEL f 
MENU LABEL ^F----ubuntu-12.04.1-Server-i386 
kernel linux/3/linux 
append root=/dev/nfs rw initrd=linux/3/initrd.gz netboot=nfs nfsroot=192.168.100.101:/mnt/asus/3 ip=dhcp

LABEL g 
MENU LABEL ^G----ubuntu-12.10-Desktop-i386 
kernel linux/2/vmlinuz 
append root=/dev/nfs initrd=linux/2/initrd.lz boot=casper netboot=nfs nfsroot=192.168.100.101:/mnt/asus/2/cd

LABEL h 
MENU LABEL ^H----ubuntu-12.10-Server-i386 
kernel linux/1/linux 
append root=/dev/nfs initrd=linux/1/initrd.gz netboot=nfs nfsroot=192.168.100.101:/mnt/asus/1

LABEL i
MENU LABEL ^I----ubuntu-12.10-Server-AMD64 
kernel linux/9/linux 
append root=/dev/nfs initrd=linux/9/initrd.gz netboot=nfs nfsroot=192.168.100.101:/mnt/asus/9/

---

