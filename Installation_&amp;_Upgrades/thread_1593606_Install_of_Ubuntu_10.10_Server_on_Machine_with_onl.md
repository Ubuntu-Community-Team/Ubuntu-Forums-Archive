---
title: "Install of Ubuntu 10.10 Server on Machine with only Serial Console"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by dmb1976 on 2010-10-11
Hi All,

I'm trying to get Ubuntu server 10.10 installed on a machine that doesn't have a graphics card installed.  My only option right now is to use a serial port as a console.

Does anyone have any tips or instructions on how I can set up the system using a serial port console?

Is there something that I can edit within the ISO to redirect the output?

Thanks in advance,

--db

---

### Post by mokachoka on 2010-10-29
Im about to do the exact same thing on a SS4200...

Search for ss4200 serial install there are some basic instructions for older versions of ubuntu... You will just have to change a few things to get it to work with 10.10...

Wish me luck... i hate blind installs.



...

also found this - [http://brainstorm.ubuntu.com/item/3215/](http://brainstorm.ubuntu.com/item/3215/)

---

### Post by gsker on 2010-11-08
I did this for lucid 10.04

I followed the instructions on [http://ss4200.pbworks.com/w/page/24235027/Ubuntu-server--9_10-amd64](http://ss4200.pbworks.com/w/page/24235027/Ubuntu-server--9_10-amd64) and installed from the net.

[SIZE="3"]As a summary:[/SIZE]

[list=1][*] Remaster the mini.iso image (I used isomaster) and [list=1]
[*] add "serial 0 115200" to the top of isolinux.cfg
[*] add "console=ttyS0,115200,8n1" to the append line in text.cfg[/list]
[*] Boot from the iso (or make a CD and boot from that)
[*] Install from the serial console.
[*] Before rebooting drop to a shell by choosing "Back" and choosing shell from the menu. Then
[LIST=1]
[*] chroot /target
[*] vi /boot/grub/grub.cfg and make sure "serial" is on a line by itself (Replace "serial --unit=0 --speed=8 --word=1 --parity=no --stop=1" with just the word "serial" or you won't get a grub menu) and "console=ttyS0" is on the kernel line. Exit vi with :"qw!" to force it.
[*] Make sure init starts a getty using this snippet: 
sed -e 's/tty1/ttyS0/g;s%^exec.*%exec /sbin/getty ttyS0 38400%g;' /etc/init/tty1.conf > /etc/init/ttyS0.conf
[*] exit chroot[/list]
[*] exit shell
[*] finish install
[*] reboot
[/LIST]

I'm still testing this procedure, so I may come back and edit this.

---

### Post by mtbsoft on 2010-12-14
> **mokachoka said:**
> Im about to do the exact same thing on a SS4200...

<snip>


also found this - [http://brainstorm.ubuntu.com/item/3215/](http://brainstorm.ubuntu.com/item/3215/)
Thank you soooooo much for the brainstorm link, I'm doing the same as you on an SS4200-E and that link had the solution to my problem.

I was able to adapt the syslinux.cfg file to update the necessary "console=ttyS0,115200n8 --" to the unetbootin files on my USB stick (I don't have a USB CD/DVD drive) to get the serial console working... it's installing as I type.

Thanks again.

---

