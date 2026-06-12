---
title: "pxe install Net4801"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by juan234 on 2008-11-17
I am trying to PXE a Soekris NET4801.  I have followed the instructions at [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

I have connected before to the net4801 with windos hyper terminal no problem.  I am now using cutecom.  I can see the output of the net4801 on my screen, but when i try to control +P nothing happens, I can't even enter "help" and there is a bunch of garble.  As far as I can tell cutecom settings are correct.  Also when the soekris goes into pxe mode it receives an IP from my dhcp server, but then stops.

CuteCom settings:
parity none
handshake options are software and/or hardware none marked.
data bits 8
stop bits 1 
open for reading and writing
baud rate 57600

So far I have installed:

inetutils-inetd (not sure what to do here) 

Dhcp server (same as pxe/apache) here is dhcp.conf

ddns-update-style none;

option domain-name-servers xx.xx.xx.xx,xx.xx.xx.xx;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

subnet 192.168.168.0 netmask 255.255.255.0 {
        range 192.168.168.200 192.168.168.205;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.168.255;
#       option routers 192.168.168.168;  This it because I am not conneting to internet, just using a switch
        filename "pxelinux.0"; 
}

TFTP  and edited /etc/inetd.conf  (do I need to turn this on?) 

tftp    dgram   udp    wait    root    /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

also have  sudo cp -r /media/cdrom/install/netboot/* /var/lib/tftpboot/

I have installed Apache and copied the files to /var/www/ubuntupxe it works when I go to my browser.

I have also installed system-config-kickstart  here is the ks.cfg file.

#Use Web installation
url --url [http://192.168.168.200/ubuntupxe](http://192.168.168.200/ubuntupxe)

This is my /var/lib/tftpboot/pxelinux.cfg/default file

include ubuntu-installer/i386/boot-screens/menu.cfg
default ubuntu-installer/i386/boot-screens/vesamenu.c32
prompt 0
timeout 0

label linux
kernel ubuntu-installer/i386/linux
append ks=http://192.168.168.200/html/ks.cfg vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16432 root=/dev/rd/0 rw  --

note that the ks.cfg is in /html 

Do all the paths look right?  Have I missed anything? The Net4801 just stops.  many thanks in advance.

---

### Post by webdr on 2008-11-24
Wow, a week w/o any replies? I guess the community is on holiday.
Ok, lets chat about your issues.

[LIST=1]
[*]CTRL+P not getting sent
[*]Not able to do boot f0
[*]Are the paths and PXE configs correct
[/LIST]

The 1st and 2nd issues are likely related. I think you may want to try 38400 8n1. 

PXE paths and configs...
From what you've provided all seems well so far, with one caveat, try to manually browse the 192.168.x.x/PXELOADER file first to double check that it is a valid destination.

Hope this helps,
-Mark

---

