---
title: "Network installation problem"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Gonzalongo on 2011-10-24
Good day to everyone,
 
I am trying to install ubuntu 11 oneiric over o local area network. It boots from pxe allright but when trying to grab the packets it fails. In the log I see this message
 
[COLOR=black]**net-retriever-xxxx- deduplicate**[/COLOR] where xxxx is a different number every time I try
 
These are the tools a I am using
 
Got a small netbook acting as a server running w7 starter
Tftpd for the pxe bit
xserver to share the folder where i unzipped the ubuntu-11-10.desktop.iso
the netboot installer of that version downloaded for ubuntu
 
The target computer is a toshiba satellite a60.
 
When I start the installer pops up, it detectes the network card, it gets and ip assigned, if I get a console I can see the server is alive and because of the logs I know the web server is doing its job.
 
I took all these pains because the computer bios wont allow to boot from usb, the cdrom drive is busted, and it wont boot from an usb external cdrom I own.
I readed somewhere that it might have to do with the gpg security check but I dont knohw how to disable signature check on the installation files ( supposing this has anything to do at all)
Any hint will be appreciated.
Thanks in advance.
Regards.
Gonzalo

---

### Post by Gonzalongo on 2011-10-28
Workaround solution.
 
After days of tinkering with the expert mode trying to make it work through ftp as well, and using too an alternate installation disk I gave up.
 
What I did is to temporarily install wubi (the target machine is a dual one with win7) and on booting up using the grub2 feature to mount iso images. As my ubuntu-desktop-11.iso was already on the hard drive is was an easy feat to acomplish, bear in mind that in order to proceed with theinstallationonce you are on the desktop you have to issue an umount order for the iso.  There is an excellent article on the matter here [http://ubuntuguide.net/install-ubuntu-without-burning-livecd-from-windows-7-dual-bootnot-wubi](http://ubuntuguide.net/install-ubuntu-without-burning-livecd-from-windows-7-dual-bootnot-wubi)    I had to use wubi to use grub2 since the boot.ini bit didnt work on my win 7 nor the bcdedit bit.
Regards.

---

