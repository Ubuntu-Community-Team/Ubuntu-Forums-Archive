---
title: "1"
date: 2004-12-05
forum: Installation &amp; Upgrades
---

### Post by geofff on 2004-12-05
I have loaded abuntu from installation cd. It has gone well except that the machine won't turn off. It goes through the closedown routine until it gets to 
"power down
acpi_power_off called"
It then hangs,

The system is athlon xp 2800 with asus A7v400 motherboard including VIA chipset.

I noted that on some VIA systems "boot: linux pci=noacpi" was suggested although what it was needed for was not stated! nor where to put it! I tried various places but finally settled on reinstalling and typing it after boot: on the first screen. 

This didn't work and the machine still hangs.

Q1 Any ideas how I can stop it hanging?
Q2 Does the "pci=noacpi" instruction need to be reversed? What does it do?

Thanks

---

### Post by alekandr on 2004-12-05
simply type

shutdown -r now   // nothing will stop this bad boy command. note this is a reboot command, you could change the -r to -h to shutdown. jsut use the reboot one and press the power off button. simple :D

---

### Post by geofff on 2004-12-05
[QUOTE=geofff]I have loaded abuntu from installation cd. It has gone well except that the machine won't turn off. It goes through the closedown routine until it gets to 
"power down
acpi_power_off called"
It then hangs,

The system is athlon xp 2800 with asus A7v400 motherboard including VIA chipset.

I noted that on some VIA systems "boot: linux pci=noacpi" was suggested although what it was needed for was not stated! nor where to put it! I tried various places but finally settled on reinstalling and typing it after boot: on the first screen. 

This didn't work and the machine still hangs.

Q1 Any ideas how I can stop it hanging?
Q2 Does the "pci=noacpi" instruction need to be reversed? What does it do?

Thanks[/QUOTE]
 Apologies  
Somehow I deleted the title before sending.
It should have read "hang on power down" not 1!

---

### Post by saBrEwolf on 2004-12-05
have you tried putting in the line in the grub commands acpi=off
like this: (This is a section from my /boot/grub/menu.lst)

splashimage=(hd0,0)/boot/grub/ubuntu_snow.xpm.gz
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

Hope this helps

---

### Post by geofff on 2004-12-05
[QUOTE=saBrEwolf]have you tried putting in the line in the grub commands acpi=off
like this: (This is a section from my /boot/grub/menu.lst)

splashimage=(hd0,0)/boot/grub/ubuntu_snow.xpm.gz
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

Hope this helps[/QUOTE]
 Thanks Craig. I have now amended ~grub/menu.lst to include acpi=off.

This has removed the " acpi_power_off called" message in the shutdown routine.

The machine now hangs after "power down"!

If its any use I get the following error messages on booting up that I have no idea what they mean
"modprobe: FATAL: error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernal/drivers/pci/hotplug/pciehp.ko): operation not permitted"
and 
"modprobe:FATAL: error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernal/drivers/pci/hotplug/shpchp.ko): operation not permitted"

---

### Post by jiyuu0 on 2004-12-05
try

acpi_power_off called
[http://kitech.com.my/ubuntu/4.10/index.html#acpipoweroff](http://kitech.com.my/ubuntu/4.10/index.html#acpipoweroff)

modprobe: FATAL: Error inserting...
[http://kitech.com.my/ubuntu/4.10/index.html#modprobefatalerror](http://kitech.com.my/ubuntu/4.10/index.html#modprobefatalerror)

---

### Post by az on 2004-12-05
This has been discussed a lot.  Look in your bios and find out if you are using apm or acpi.  If you can use apm, add the word
apm
to your /etc/modules file.  You need root priveledges to do this.  Open a console and type sudo gedit /etc/modules.

Post what your bios says.

---

### Post by geofff on 2004-12-06
jiyuu0 and azz thanks for the help

I followed the kitech.com instructions above. They worked like a dream. 

Sorry if this has been discussed before. I did search but didn't find the answer. I hadn't found kitech. 

Thanks again

Geofff

---

