---
title: "Strange grub menu behaviour."
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by smileyz on 2013-02-01
Hello everyone!
I'v faced with some strange grub2 boot behavior.

Wanted to see the booting process and not the purple screen I removed **splash** and **quiet** from in **/etc/default/grub**, so **GRUB_CMDLINE_LINUX_DEFAULT="" **and regenerated **grub.cfg**.
Also set grubmenu to apear by default and wait for 10 sec and not pressing shift-key every boot.

So menu entry at grub.cfg looks like that:
```
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode **<-- not commented**
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c8e8ee52-ef16-42b8-ba2a-38c797f960d4
    linux    /vmlinuz-3.2.0-32-generic-pae root=UUID=2e3beed6-70f3-439e-be1f-b212b37adb32 ro **<-- ok, no splash and quiet**
    initrd    /initrd.img-3.2.0-32-generic-pae
```Ok now rebooted and get grub menu:

```
Ubuntu, with Linux 3.2.0-32-generic-pae
Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)
<...>
```If I _***do nothing***_ and just let grub start default 0 entry after 10 sec timeout, I see ***_no_*** kernel booting messages instead there is a purple screen there till the service boot messages apear.
If I press <e> such way going to edit first record, then _***do not edit anything ***_and pres <ESC>(leaving edit mode) and press <ENTER> I _***do see***_ kernel messages there and no purple fog.
If I press <e> such way going to edit first record, then _***do not edit anything ***_ and pres Ctrl-X for booting I _***do see***_ kernel messages there.

So without any changes seems entering and leaving menu entry somehow generates different kerenl args listO.o?

Okey. Now if I comment *gfxmode* in **grub.cfg** so it becomes like that:
```

menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    **#gfxmode $linux_gfx_mode <-- now commented**
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c8e8ee52-ef16-42b8-ba2a-38c797f960d4
    linux    /vmlinuz-3.2.0-32-generic-pae root=UUID=2e3beed6-70f3-439e-be1f-b212b37adb32 ro **<-- ok, no splash and quiet**
    initrd    /initrd.img-3.2.0-32-generic-pae
```everything boots like a charm with kernel messages.


I can reproduce that on two(has only two with ubuntu) PC (one desktop and lenovo notebook) with 100% rate.

It is not the problem for me to create correct grub.cfg which boots with kerenel log, but, I dont understand 
how it comes that entering menuentry and leaving *_**without**_* changes differs in behaviour with default grub boot for the same entry.

 I can do any dump because can reproduce it, as I wrote, with 100% rate.

Ps
To be honest I'v come to that after PC with fresh installed ubuntu freezed on purple screen and i wanted at first step to see what is going on under the hood.
Removing the purple fog gives clear boot, so the problem is somehow connected with that mode. I'v googled some similar problesm on the web(dated jan-march of the 2012) but Ill fix it in details a bit later.
It is not the problem at the moment and not the question. The questions is WHY does grub boot behave different?

---

