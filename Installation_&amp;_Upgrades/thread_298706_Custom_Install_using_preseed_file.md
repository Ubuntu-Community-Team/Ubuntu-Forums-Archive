---
title: "Custom Install using preseed file"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by craftybones on 2006-11-13
Hello,

I am currently trying to create a custom CD so that I can install over multiple servers. I followed the example provided on the Ubuntu wiki and I am a little unsure as to whether it is doing what I think it is supposed to be doing. 

For starters, here is the link to the wiki:

[https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo](https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo)

According to this example, the locale and keyboard selections are "automated". However, at the time of install it takes me to a selection screen offering all me my selections of locale and keyboard as default choices. My peeve is that it doesn't actually "select" them. in other words, I have to actually hit enter in order to select them.

Am I missing something? Do I have to set DEBCONF_PRIORITY to critical for it to stop annoying me with silly questions? 

Here is my isolinux.cfg:

```
moonwolf@moonwolf:~$ cat /opt/cd-image/isolinux/isolinux.cfg
    DEFAULT /install/vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND   initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL install
  menu label ^Install in text mode
  kernel /install/vmlinuz
  append   initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL linux
  menu hide
  kernel /install/vmlinuz
  append   initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL cdrom
  menu hide
  kernel /install/vmlinuz
  append   initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL expert
  menu hide
  kernel /install/vmlinuz
  append   DEBCONF_PRIORITY=low initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw --
LABEL oem
  menu label Install in ^OEM mode
  kernel /install/vmlinuz
  append  anna/choose_modules=oem-config-udeb initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL server
  menu label Install a ^server
  kernel /install/vmlinuz
  append  preseed/file=/cdrom/preseed/server.seed initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw --
LABEL server-expert
  menu hide
  kernel /install/vmlinuz
  append  preseed/file=/cdrom/preseed/server.seed DEBCONF_PRIORITY=low initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw --
LABEL check
  menu label ^Check CD for defects
  kernel /install/vmlinuz
  append  MENU=/bin/cdrom-checker-menu initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL rescue
  menu label ^Rescue a broken system
  kernel /install/vmlinuz
  append  rescue/enable=true initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
[B]LABEL custom_pressed
  menu label ^Install customized ubuntu
  kernel /install/vmlinuz
  append preseed/file=/cdrom/preseed/server.seed debian_installer/locale=en_US kbd-chooser/method=us initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --[/B]

DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

 
```

I've highlited the change I made to the default isolinux.cfg.

As you can see, I am not really "customizing" as of now. I am pointing to the default server.seed file. I just want this to work before I can proceed with other parts of the customization.

Thank you,

craftybones

---

### Post by craftybones on 2006-11-13
setting DEBCONF_PRIORITY did the trick, but please let me know if there is any other way? I've set it to critical currently.

crafty

---

### Post by orvils on 2007-06-25
I think this is the way to work with the default answers:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/preseed-intro.html#preseed-seenflag](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/preseed-intro.html#preseed-seenflag)

---

