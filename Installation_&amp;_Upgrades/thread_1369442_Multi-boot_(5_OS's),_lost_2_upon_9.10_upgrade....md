---
title: "Multi-boot (5 OS's), lost 2 upon 9.10 upgrade..."
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-01-01
I lost my FC10 and PCLinuxOS 2007. Ubuntu 9.10 64bit is good, as is XP and Vista.

What's the repair procedure?

My old menu.lst was this:

> 
## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro quiet splash noapic irqpoll noirqdebug
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro quiet splash noapic irqpoll noirqdebug
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

title           FC8
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.26.8-57.fc8
initrd          /boot/initrd-2.6.26.8-57.fc8.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        XPPro
root        (hd0,0)
savedefault
makeactive
chainloader    +1

title           Windows Vista
root            (hd1,0)
savedefault
makeactive
chainloader     +1

title           PCLOS
kernel          (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5  acpi=on resume=/dev/sda7 splash=silent vga=788
initrd          (hd1,4)/boot/initrd.img

title           PCLOS GRUBloader
root            (hd1,4)
configfile      /boot/grub/menu.lstand where do I find the new menu.lst?


Is this it???

Failed boots in RED

> 
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d6ac129bf4974a14
    drivemap -s (hd0) ${root}
    chainloader +1
}
[COLOR=Red]menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.26.8-57.fc8 root=/dev/sda4[/COLOR]
}
[COLOR=Red]menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.27.19-170.2.35.fc10.i686 root=/dev/sda4[/COLOR]
}
[COLOR=Red]menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686 root=/dev/sda4[/COLOR]
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set fefeb4a2feb4549d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 10fca6f2fca6d0f0
    chainloader +1
}
[COLOR=Red]menuentry "PCLOS (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5 acpi=on resume=/dev/sda7 splash=silent vga=788
    initrd (hd1,4)/boot/initrd.img[/COLOR]
}
menuentry "linux-nonfb (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sdb5 acpi=on resume=/dev/sda7
    initrd (hd1,4)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sdb5 failsafe acpi=on resume=/dev/sda7
    initrd (hd1,4)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###
Is it just a matter of editing partition numbers, as the old menu.lst???

---

### Post by mr clark25 on 2010-01-01
i dont know if that is the new menu.lst or not.

in grub2, i know it is found here: /boot/grub/menu.lst

i would run update-grub. it worked for me. but then again, i dont have 5 os's

command:
update-grub

---

### Post by Moozillaaa on 2010-01-01
Alright - I rebooted, brought up the menu, and clicked on my FC10 entry to edit the line, and changed from this:


[B][I]menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,[SIZE=4]4[/SIZE])
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.26.8-57.fc8 root=/dev/sda4
[/I][/B]

to 


[B][I]menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,[SIZE=4][COLOR=Red]3[/COLOR][/SIZE])
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.26.8-57.fc8 root=/dev/sda4[/I][/B]

It started loading files, and stopped at:

[COLOR=Navy][B]VFS: Cannot open root device "sda4" or unknown-block (0, 0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel Panic - not syncing: VFS Unable to mount root FS on unknown-block (0, 0)[/B][/COLOR]

---

### Post by mr clark25 on 2010-01-01
did you try update-grub?

that is what i would do...

---

### Post by Moozillaaa on 2010-01-01
No - I haven't done a GRUB update yet... I'd like to know what's wrong first, *UNLESS*

and now I'm remembering an error when I did the first update after installing yesterday:

What does this error mean?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141981&d=1262329833[/IMG]

---

### Post by Moozillaaa on 2010-01-01
No 'luck'.

> chuckbhp@chuckbhp-laptop:~$ sudo update-grub
[sudo] password for chuckbhp: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Fedora release 10 (Cambridge) on /dev/sda4
Found Windows Vista (loader) on /dev/sdb1
Found Windows Vista (loader) on /dev/sdb2
Found PCLinuxOS release 2007 (PCLinuxOS) for i586 on /dev/sdb5
done
chuckbhp@chuckbhp-laptop:~$ 

Same partitions/OS's will not boot; the error is the same:


[COLOR=Navy][B]VFS: Cannot open root device "sda4" or unknown-block (0, 0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel Panic - not syncing: VFS Unable to mount root FS on unknown-block (0, 0)[/B][/COLOR]

---

### Post by mr clark25 on 2010-01-01
> **Moozillaaa said:**
> 
[COLOR=Navy][B]VFS: Cannot open root device "sda4" or unknown-block (0, 0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel Panic - not syncing: VFS Unable to mount root FS on unknown-block (0, 0)[/B][/COLOR]

you may need to select the ones that dont work and press "c" to enter a command line. then type this:

setroot=(hd0,3)

if that still doesnt work, try this:

setprefix=(hd0,3)/boot/grub

change (hd0,3) to which partition you are trying to restore. 
                x,y
x is which hard drive, and y is which partition.

hope that helps. if it still doesn't work, this problem is beyond me :(

---

### Post by oldfred on 2010-01-01
With grub2 there is no menu.lst it is now grub.cfg and is created on every update-grub and is not to be edited. If you want to edit entries you add them to 40_custom and update grub adds the entries to grub.cfg.

Partition numbering has changed. Grub legacy (0.97) started at 0 zero and grub2 (1.97 beta4 currently) starts at 1 one.  

I have seen several cases where grub2 misses the init line for some other operating systems. With many operating systems it is often best to install that operating systems grub to the partition and chainboot from grub2 entry in 40_custom.

menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1
}

Since you still have your old grub entries you can copy the new entries into 40_custom and edit them to be like you old entries UUIDs & sdax but in the new style of grub2. Just remember the partition numbers have changed (hd0,0) is now (hd0,1). Once they are working you can turn off os prober so you do not have duplicate entries.



[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

---

### Post by Moozillaaa on 2010-01-01
> **oldfred said:**
> With grub2 there is no menu.lst it is now grub.cfg and is created on every update-grub and is not to be edited. If you want to edit entries you add them to 40_custom and update grub adds the entries to grub.cfg.

Partition numbering has changed. Grub legacy (0.97) started at 0 zero and grub2 (1.97 beta4 currently) starts at 1 one.  

I have seen several cases where grub2 misses the init line for some other operating systems. With many operating systems it is often best to install that operating systems grub to the partition and chainboot from grub2 entry in 40_custom.

menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1
}

Since you still have your old grub entries you can copy the new entries into 40_custom and edit them to be like you old entries UUIDs & sdax but in the new style of grub2. Just remember the partition numbers have changed (hd0,0) is now (hd0,1). Once they are working you can turn off os prober so you do not have duplicate entries.



[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)


Very good info here - thanks!

Will apply when I fire that machine shortly...

---

### Post by oldfred on 2010-01-01
This entry looks real mixed up unless you have a separate boot partition that is in one of the other partitions.

[COLOR=black]menuentry "PCLOS (on /dev/sdb5)" {
    insmod ext2
    set root=([COLOR=Red]hd1,5[/COLOR])
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=/dev/[COLOR=Red]sdb5[/COLOR] acpi=on resume=/dev/[COLOR=Red]sda7[/COLOR] splash=silent vga=788
    initrd ([COLOR=Red]hd1,4[/COLOR])/boot/initrd.img
}[/COLOR]

I would think everything should be (hd1,5) and sdb5??

---

### Post by Moozillaaa on 2010-01-01
> **oldfred said:**
> With grub2 there is no menu.lst it is now grub.cfg and is created on every update-grub and is not to be edited. If you want to edit entries you add them to 40_custom and update grub adds the entries to grub.cfg.

Partition numbering has changed. Grub legacy (0.97) started at 0 zero and grub2 (1.97 beta4 currently) starts at 1 one.  

I have seen several cases where grub2 misses the init line for some other operating systems. With many operating systems it is often best to install that operating systems grub to the partition and chainboot from grub2 entry in 40_custom.

menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1
}

Since you still have your old grub entries you can copy the new entries into 40_custom and edit them to be like you old entries UUIDs & sdax but in the new style of grub2. Just remember the partition numbers have changed (hd0,0) is now (hd0,1). Once they are working you can turn off os prober so you do not have duplicate entries.



[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

> 
[LIST]
[*]If GRUB 2 cannot find the referenced kernel, try replacing the UUID with the device name (example: /dev/sda6 ). 
[/LIST]


Alright, if I drop the ID #, and insert /dev/sdax instead, exactly how will the syntax be?

[B][I]FROM:

menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,[SIZE=2]4[/SIZE])
    search --no-floppy --fs-uuid --set [COLOR=Red]e167cb3e-f1fc-4852-804a-a22457aece41[/COLOR]
    linux /boot/vmlinuz-2.6.26.8-57.fc8 root=/dev/sda4

TO:

[/I][/B][B][I]menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,[SIZE=2]4[/SIZE])
[COLOR=Black]
[/COLOR]     [COLOR=Gray][COLOR=Black]??? ... /dev/sda4[/COLOR]
[/COLOR]
    linux /boot/vmlinuz-2.6.26.8-57.fc8 root=/dev/sda4
[/I][/B]

---

### Post by Moozillaaa on 2010-01-02
FC10 entry needed image file 'pointer' - see post #1, PCLOS boot error plain as day also in post #1.

Lotta' help, but both of 'em I got all by myself uh HUH....:guitar: YUP.

---

