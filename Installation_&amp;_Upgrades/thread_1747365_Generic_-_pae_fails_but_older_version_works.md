---
title: "Generic - pae fails but older version works"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by eakergd on 2011-05-02
Hello,

After a massive meltdown with the upgrade, I finally got the system put back together. Had to reinstall grub. It now defaults to a version that says "Generic - pae". When choosing this from the grub menu, it always hangs on the Ubuntu splash screen; however, I found that when I choose "previous Linux versions" from the grub menu, then choose the Ubuntu-generic, everything works fine - other than my initial bad impression of unity - but it works, at least.

Can anyone tell my why my default choice in grub doesn't work, and what I need to do to fix it? Below is a cut and paste from  /boot/grub/grub.cfg. The first entry is the one that does NOT work, and the first entry after "submenu" is the entry that DOES work.

Thanks.

menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 75c04589-cbd2-419b-b184-a716feb69d78
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=75c04589-cbd2-419b-b184-a716feb69d78 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}

---

### Post by eakergd on 2011-05-02
bump - help please

---

### Post by oldfred on 2011-05-02
there were some bugs related to this. Have you tried just editing the vt.handoff=7 out. At grub menu, use e for edit and remove it.

You are using splash so I do not know if this applies.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686)
This is a bug in our grub2 packaging; we shouldn't include vt.handoff=7 if splash isn't going to be used.

grub2 configuration has vt.handoff=7 even when X11 is not installed
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658)

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by eakergd on 2011-05-03
Nope, sorry. That didn't work.

---

### Post by ben2talk on 2011-05-11
The 'fix' for me was to look under the 'older versions'

Actually it's NOT older, I'm using the same 2.6.38-8-generic (simply without the -pae extension).

The problem with pae is that video goes out as it loads.

____________________________________________________________________

Update - FIXED**[COLOR="SeaGreen"][/COLOR]**. This is an upgrade installation issue!

Open Synaptic and install the following:

linux-image-2.6.38-8-generic-pae
linux-generic-pae linux-headers-generic-pae 
linux-image-generic-pae 
linux-headers-2.6.38-8-generic-pae

REBOOT to complete the upgrade and select the pae (which is now correctly installed).

---

