---
title: "Lost grub MBR on an encrypted system"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by damatta on 2010-03-06
Hello.

During a repair windows did overwrite my grub MBR for it's own bootloader. Now how do I get back to my encrypted ubuntu?

Thanks

---

### Post by stlsaint on 2010-03-06
You just need to reinstall grub. See my signature for links.

---

### Post by damatta on 2010-03-06
Thanks for the reply.
I used Super Grub Disk which appeared to have retrieved /boot/menu.lst however when I pick Ubuntu kernel it does display the content then hangs. It does mention something about "file not found". What am I missing here?

---

### Post by Herman on 2010-03-07
The commands you would normally use to boot with are contained in your /grub/menu.lst file and those will be a little bit different from the commands we use for most ordinary installations, and which are used in Super Grub Disk.

I guess you're using GRUB Legacy by the fact that you mentioned menu.lst instead of grub.cfg, but here's an example of what I mean, 

> menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0f85cb9d-c0af-4da4-9a1a-512d1e49d3d4
    linux    //vmlinuz-2.6.32-10-generic **root=/dev/mapper/usb--crypt--lynx-root ro **elevator=noop  quiet splash
    initrd    //initrd.img-2.6.32-10-genericThe part you see here in bold will be similar regardless of whether you're using GRUB Legacy or GRUB2, and yours will be different from mine anyway.
You probably need to take a look at your own GRUB's menu.lst file somehow, (with a live CD or by using GRUB from the command line, and copy what you need from your menu.lst and use the same for booting with. [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli")

You may be find it easier to do a 'configfile boot' with Super Grub Disk'. With a 'configfile boot', Super Grub Disk will read your own system's menu.lst and boot from it. I'm not sure if I can remember what adrian15 calls a configfile boot but you should be able to find it somewhere in Super Grub Disk's menus. It might be something like 'cat menu.lst and boot' or similar.

---

### Post by perham on 2010-03-07
> **Herman said:**
> The commands you would normally use to boot with are contained in your /grub/menu.lst file and those will be a little bit different from the commands we use for most ordinary installations, and which are used in Super Grub Disk.

I guess you're using GRUB Legacy by the fact that you mentioned menu.lst instead of grub.cfg, but here's an example of what I mean, 

The part you see here in bold will be similar regardless of whether you're using GRUB Legacy or GRUB2, and yours will be different from mine anyway.
You probably need to take a look at your own GRUB's menu.lst file somehow, (with a live CD or by using GRUB from the command line, and copy what you need from your menu.lst and use the same for booting with. [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli")

You may be find it easier to do a 'configfile boot' with Super Grub Disk'. With a 'configfile boot', Super Grub Disk will read your own system's menu.lst and boot from it. I'm not sure if I can remember what adrian15 calls a configfile boot but you should be able to find it somewhere in Super Grub Disk's menus. It might be something like 'cat menu.lst and boot' or similar.

first enter into grub's command line by pressing c in the menu. then enter these commands to retrieve your own menu.lst :

root (hdX,Y) <-- your /boot partition
configfile /boot/grub/menu.lst


then you see your own grub menu.

to reinstall grub, run these commands:

root (hdX,Y)
setup (hdX,Y) <-- installs grub on your partition 
OR setup (hdX) <-- installs grub on the mbr.

and you should be able to boot into your system.

---

### Post by damatta on 2010-03-07
Thank you all but i still havent made it.
Super Grub Disk tries to boot but mistakes the kernel name and location, as I have hd0,2 (encrypted root) and hd0,5 (boot)

I'll see if I'm able to mount this encrypted partition on windows.

---

