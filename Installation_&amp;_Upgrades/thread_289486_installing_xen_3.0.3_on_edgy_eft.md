---
title: "installing xen 3.0.3 on edgy eft"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by thatwouldbeme on 2006-10-31
Hi there,

I am a windows power user finally switching to linux.  I'm choosing ubuntu not necessarily because it's the most powerful but because I want to understand it inside and out in order to be able to support the migration of non-power users around me to it, as it seems the most viable non-ms option for them.  however, I definitely want to power use ubuntu to the bone.

on that note, the first project I'm doing on my shiny new edgy eft box is trying to set up xen.  due to my limited experience I was sticking pretty close to a tutorial but got stuck when it was time to add loop devices.  I don't find a file at /etc/mkinitramfs folder.  is this because I installed the desktop distribution instead of the server?  (btw, this is a separate box designated specifically for ubuntu work, so fixes like "wipe your drive, repartition, and reinstall the other distro" are actual options for me: my data is safe and sound).  what is mkinitramfs, and/or where else can add my loop devices?

thanks in advance,
thatwouldbeme

---

### Post by cinderdust on 2006-11-13
mkinitramfs is an executable that makes a ram disk for system to use during boot.  Stands for 'MaKeINITialRAMFileSystem" I think ;)

It's at /usr/sbin/mkinitramfs (on dapper which I am using now).
You use it to create a module need for boot.
example: this is from grub config /boot/grub/menu1st
--- portion of grub code that allows xen boot  ---
title           Xen 3.03 / XenLinux 2.6
root            (hd0,0)
kernel          /boot/xen-3.0.gz dom0_mem=196608 console=vga
module          /boot/vmlinuz-2.6-xen root=/dev/hda1 ro
module          /boot/initrd.img-2.6.16-29-xen
boot
---- end ---
You use mkinitramfs to create 'initrd.img-2.6.16-29-xen'
--- LIKE SO --
cd /boot
mkinitramfs -o initrd.img-2.6.16-29-xen 2.6.16-29-xen
--- end ---
The last part  "2.6.16-29-xen"  refers to a directory /lib/modules/2.6.16-29-xen which comes with xen distro.

---

### Post by Klunk on 2006-11-25
I have been using Ubuntu for a few versions now and I decided now was the time to upgrade to edgy eft. I have used new hardware and built the machine as a server build. I am now 'playing' with xen 3.0.3 but I am having a problem. I have looked on a number of how-to sites and followed Hack #90 in the O'Reilly Ubuntu Hacks book and yet I am getting an error. for some reason it is complaining about root=/dev/sda1 on the modules line when I try to boot with my grub spec.

The stanza looks like this:

```

title        Ubuntu Xen static
root         hda(0,0)
kernel       /boot/xen-3.0.3-0.gz console=vga
module       /boot/vmlinuz-2.6-xen root=/dev/sda1 ro console=tty0

```    

I am using an ABIT NF7-S mobo with Athlon 3200XP processor and 1GB RAM and booting from a 250GB SATA drive. It boots edgy fine.

I downloaded the xen binaries rather than build them from sources.

Thanks
for any help people can offer here, I have spent several hours trying to get this to work without success.

---

### Post by cinderdust on 2006-11-25
I started using ubuntu about 4 weeks ago when I wanted to test Xen and didn't want to pay RedHat. I also installed xen 3.0.3 from binary.  I read the 'manual' from the xen website but that wasn't enuf.  I found this how-to very useful. It's for dapper but  I suspect it is still relevant for edgy :)
 [http://www.ubuntuforums.org/showthread.php?t=196124&highlight=xen+dapper](http://www.ubuntuforums.org/showthread.php?t=196124&highlight=xen+dapper)

---

### Post by Klunk on 2006-11-26
Thanks for this pointer, I now have a running baseline domU.

I now have a further question, does anyone know how I can make that baseline a server build of Ubuntu? Plus, I have 2 NICs has anyone tried setting up a system with 2 NICs on 2 networks. 

The plan is that this machine will run multiple domUs, one will be a DHCP server with DNS (only using 1 NIC), one will be a firewall/gatesway (utilizing both NICs), one will run a web proxy (1 NIC) and one will run a mail server (1 NIC). All machines that go outside the domain will go via the firewall/gateway machine. I was having a little trouble setting up eth1 and added a static entry into /etc/network/interfaces but that stopped eth0 working as well.

---

