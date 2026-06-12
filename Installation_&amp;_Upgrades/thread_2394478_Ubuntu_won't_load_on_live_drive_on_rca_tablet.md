---
title: "Ubuntu won't load on live drive on rca tablet"
date: 2018-06-16
forum: Installation &amp; Upgrades
---

### Post by christopher-acosta-af on 2018-06-16
I have an RCA cambio (W101SA23T1S) and a live drive with Ubuntu in it won't load. It won't even bring up any GUI whatsoever. This live drive does work in other systems. I thought Ubuntu had added support for uefi 32 in a 64bit CPU. I know secure boot is off and I tried both 32 and 64 bit versions. I've been trying other distros on this thing and nothing seems to boot. What can I do?

---

### Post by christopher-acosta-af on 2018-06-18
Bump

---

### Post by oldfred on 2018-06-18
You need to manually add the 32 bit UEFI boot loader bootia32.efi both to installer & once installed.
Ubuntu does not include that file in its distribution.
Some older instructions may have compliling your own, but you just need to download the file.

       32 bit UEFI
[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)
[https://askubuntu.com/questions/392719/32-bit-uefi-boot-support](https://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

---

### Post by westie457 on 2018-06-18
On this machine is the Usb C port used to charge it?
If so it is possibly the only port you can boot from.
I suggest you purchase an OTG Usb C cable or a dual Usb drive like this one. [https://www.sandisk.co.uk/home/mobile-device-storage/ultra-dual-drive-usb-type-c](https://www.sandisk.co.uk/home/mobile-device-storage/ultra-dual-drive-usb-type-c)

---

### Post by christopher-acosta-af on 2018-06-20
> **oldfred said:**
> You need to manually add the 32 bit UEFI boot loader bootia32.efi both to installer & once installed.
Ubuntu does not include that file in its distribution.
Some older instructions may have compliling your own, but you just need to download the file.

       32 bit UEFI
[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)
[https://askubuntu.com/questions/392719/32-bit-uefi-boot-support](https://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

Yeah i tried that now, but it still didn't work. it's doing the same it did before. to clarify, i get to see grub )both before and after trying the bootia32.efi) but once i hit live mode i get a terminal looking string saying "i8042: Can't read CTR while initializing i8042
[drm:pwm_setup_backlight [i915]] *ERROR* Failed to own the pwm chip"

and then a whole bunch more errors about a device not accepting address.

---

### Post by oldfred on 2018-06-20
This error seems related to not finding a ps/2 port.
[https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-c05067507&docLocale=en_US](https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-c05067507&docLocale=en_US)

Do you have your keyboard & mouse connected to ps/2 ports? If not it can be ignored.
There are a variety of threads on backlight, some have solutions, but it depends on hardware.

So can you boot with 64 bit UEFI? and do not need the 32 bit UEFI?
You may need other boot parameters, but with low cost proprietary system, there may be unique hardware that is not supported.
[https://laptoping.com/specs/product/rca-cambio-w101sa23t1s/](https://laptoping.com/specs/product/rca-cambio-w101sa23t1s/)

It looks like standard Ubuntu will not work.
[https://github.com/devinsmith/rca-cambio-linux](https://github.com/devinsmith/rca-cambio-linux)

Do not know if Lubuntu will now work, as it is for lightweight systems.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

