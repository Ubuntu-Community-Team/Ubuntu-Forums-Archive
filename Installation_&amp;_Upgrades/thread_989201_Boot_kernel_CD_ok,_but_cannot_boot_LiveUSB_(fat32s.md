---
title: "Boot kernel CD ok, but cannot boot LiveUSB (fat32/squashfs)"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by vanjeje on 2008-11-21
Hello,

I want to use my wife's old notebook without USB BIOS support (USB is totally inactive at startup) to start a LiveUSB stick. I do not want to install Ubuntu on the  

I have created a Boot CD with a kernel and some modules, using tutorials, [BootUSBFromCD]("https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD"), and especially [CD de Boot pour les amateurs de cambouis]("http://fausse-piste.net/piste1/spip.php?article157").
This is great, I have even added some modules to support my Pcmcia USB2 card (initially only USB1 of the computer was usable).

But this seems to work only on a complete Ubuntu installation on the USB Stick. On the LiveUSB startup disk created from Ubuntu 8.10 LiveCD, there are only the files in a fat32 partition. Adding squashfs in the modules for the Boot CD is not enough. There must be a special way of booting in this case.
How can I have my Boot CD with USB activation start the squashed system on the LiveUSB stick ?

(hints : currently, the startup process last stage ends with
```
Begin: Running /scripts/local-premount ...
Done.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: mount /sys on /root/sys failed: No such file or directory

Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox ... (ash)
...
(initramfs)
```

In the /root I can find LiveUSB files, for instance /root/casper with the squashfs system in it...

Thanks in advance for any piece of advise.

---

### Post by vanjeje on 2008-11-21
Well, I looked at the netboot configuration, since it is similar.
There is just an additional "boot=casper" for grub's kernel load line, in order to boot the LiveUSB (created from Ubuntu 8.10 Desktop LiveCD utility).

Sum up : in order to create a kernel boot CD, this [tutorial]("http://fausse-piste.net/piste1/spip.php?article157").

I made two "lsmod", before and after putting in my Pcmcia USB2 card with my USB stick, and a "diff" to see which modules where added. I also added squashfs and aufs, and some others, I wonder which ones are really required.
My modules, in /etc/initramfs-tools/modules :
```
usbcore
sd_mod
yenta_socket
rsrc_nonstatic
pcmcia_core
ehci_hcd
uhci_hcd
ohci_hcd
usb-storage
scsi_mod
fat
vfat
loop
squashfs
aufs
exportfs
```

my grub menu.lst :
```
title          Ubuntu
root           (cd)
kernel         /boot/vmlinuz-usb root=/dev/sdb1 boot=casper ro quiet splash
initrd         /boot/initrd-usb.img
boot
```

If you add "persistent" to the kernel line, and you have a labelled "casper-rw" partition (will it also work on the "casper-rw" file created by the LiveUSB utility?), you will be able to keep your changes on the LiveCD session.
I hope I will be able to start my liveUSB on multiple computers, with or without USB BIOS support.

It seems somehow magic to me, so I would appreciate some useful documentation on how linux is starting.

---

### Post by martinbaselier on 2008-11-22
Today I had to do some repartitioning on my laptop and I found my ODD stopped working (must have happened sometime in the last few months.) but anyway I had to boot from a usb-stick, which my BIOS does not support. 

So I pressed c in grub and used my usb-stick created with ubuntu 8.10.
root     (hd1,0)
chainloader +1
boot 
Which basically threats the device as if it was bootable.

And I had the same problem as vanjeje. the stick seemed to boot normally but I ended in a intramfs-prompt. 

I removed everything from the usb-stick (including hidden files and then used a iso from xubuntu 8.04 on the stick. same problem. Erased everything again and now used the iso from ubuntu 8.10 and it worked. 

Not really a technical insight, but maybe it will help you solve the problem. 

FYI:
When I created the image from the live CD after booting from HDD on my ubuntu intrepid desktop-pc I got an error and it did not finish creating the stick (I think, I have not tested booting from it that way)

---

