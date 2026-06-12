---
title: "sr_mod for dvd drive to use ide-cd of old pata driver set-howto"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by deepclutch on 2007-11-03
Hai there,
I am using Ubuntu Feisty on one of the machine with 2.6.20-386 kernel on an intel HT 2.8Ghz machine.after installation the same problem of ide-pata dvdwriter detected as/or emulated as scsi by new libata drivers using module** sr_mod** and set device as **/dev/sr0**.:confused:
So,I modprobed ide-cd and blacklisted forcefully(yes using /etc/modprobe.d/00.local) and added ide-cd to /etc/modules file.but still the device /dev/scd0 or /dev/sr0 are made by udev.So Is there any way to make Ubuntu udev and other systems to make ide-cd as the module for cdrom:-?

I know there is the kernel initrd image that too have something to do with sr_mod been used for my dvdwriter.but i need hdparm and to enable DMA,the old drivers.
Somebody can help me?Thanks all.:)

---

### Post by deepclutch on 2007-11-07
BBBUMMMPP! 
someone atleast share their knowledge in how to prevent sr_mod(scsi emu) from loading and ide-cd be instead used.if i modprobe ide-cd,
lsmod o/p shows cdrom=>uses sr_mod,ide-cd :( pls help out as n the FOSS spirit :)

---

### Post by deepclutch on 2007-11-09
some developers atleast answer this.how can i make the system use ide-cd module be used by kernel :(

---

