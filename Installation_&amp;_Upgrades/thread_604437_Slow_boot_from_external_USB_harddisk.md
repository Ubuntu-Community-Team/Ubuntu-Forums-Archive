---
title: "Slow boot from external USB harddisk"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Clouds® on 2007-11-06
Hello all!

I installed Ubuntu some days ago onto an external usb harddisk.
[edit]
Installed the previous version (don't know the name) and since then upgraded to newest version when the upgraded manager suggested that....
[/edit]
The only problem I have with this installation is that the initial part of the boot process is taking a long time.

Installation procedure I followed:
- Put in live cd
- Start installation with desktop icon
- Have the installer use free space on the external usb hdd (named as hdc)
- In advanced options, I noticed that grub would be installed to (hd0). I changed nothing there.
- After installation finished, computer restarted (and booted into Windows).

So, to get my computer to boot into Ubuntu, I changed the boot sequence in the BIOS.
I tried several options, only 2 work, but very slowly.....

- Changed boot sequence to boot from HDD device, changed boot order to try the external drive first.
   Result (text on screen while booting):  'Boot from CD: error while loading operating system'

- Changed boot sequence to boot from USB-HDD device first (this is different from option above)
   Result: 'Boot from CD: NTLDR missing. Press CTRL-ALT-DEL to reboot.'

- Changed boot sequence to boot from USB-FDD or USB-CDROM
   Result: After 10-15 seconds Grub loads. After selecting to load Ubuntu in Grub, there's about 3 mins just a blinking cursor (and the disk activity light blinking about once per second). After that Ubuntu is 'starting up', and Ubuntu loads fine in a normal way (e.g. with normal speed).

I've read several posts about getting Ubuntu to boot from external drives, and some suggested to edit etc/initramfs.conf to include USB support early in the boot process. However, I can't seem to find this file to edit it.....

Anyone have any suggestion what might make the boot process faster?
Please note that I'm new to Ubuntu (and Linux).....

Thanks in advance for any reactions!

Best regards,
Clouds®

---

### Post by Clouds® on 2007-11-06
To be complete: I'm running Gutsy....I remembered the wrong name and couldn't check while writing the first post (while at work)...

Best regards,
Clouds®

---

### Post by LinuxGuy1234 on 2007-11-06
> **Clouds® said:**
> Hello all!

I installed Ubuntu some days ago onto an external usb harddisk.
[edit]
Installed the previous version (don't know the name) and since then upgraded to newest version when the upgraded manager suggested that....
[/edit]
The only problem I have with this installation is that the initial part of the boot process is taking a long time.

Installation procedure I followed:
- Put in live cd
- Start installation with desktop icon
- Have the installer use free space on the external usb hdd (named as hdc)
- In advanced options, I noticed that grub would be installed to (hd0). I changed nothing there.
- After installation finished, computer restarted (and booted into Windows).

So, to get my computer to boot into Ubuntu, I changed the boot sequence in the BIOS.
I tried several options, only 2 work, but very slowly.....

- Changed boot sequence to boot from HDD device, changed boot order to try the external drive first.
   Result (text on screen while booting):  'Boot from CD: error while loading operating system'

- Changed boot sequence to boot from USB-HDD device first (this is different from option above)
   Result: 'Boot from CD: NTLDR missing. Press CTRL-ALT-DEL to reboot.'

- Changed boot sequence to boot from USB-FDD or USB-CDROM
   Result: After 10-15 seconds Grub loads. After selecting to load Ubuntu in Grub, there's about 3 mins just a blinking cursor (and the disk activity light blinking about once per second). After that Ubuntu is 'starting up', and Ubuntu loads fine in a normal way (e.g. with normal speed).

I've read several posts about getting Ubuntu to boot from external drives, and some suggested to edit etc/initramfs.conf to include USB support early in the boot process. However, I can't seem to find this file to edit it.....

Anyone have any suggestion what might make the boot process faster?
Please note that I'm new to Ubuntu (and Linux).....

Thanks in advance for any reactions!

Best regards,
Clouds®

You can try it on your hard drive, but use CAUTION! You may dump Windows! Be careful. BTW, modprobe the USB stuff, add it to /etc/modules and re-generate your kernel.

---

### Post by Clouds® on 2007-11-07
> **LinuxGuy1234 said:**
> You can try it on your hard drive, but use CAUTION! You may dump Windows! Be careful. BTW, modprobe the USB stuff, add it to /etc/modules and re-generate your kernel.

Thanks for your reaction.
I have no idea what to do with the modprobe stuff (other than type modprobe usbcore in a terminal?) or how to regenerate the kernel.

However, I managed to destroy the Ubuntu installation when following a guide that aims to have Ubuntu load from an usb-hdd.

And then, when reinstalling Ubuntu to the usb-hdd again, I managed to destroy my Windows too (dunno why, afaik I used exact same procedure as first installation of Ubuntu, yet this time Grub was not placed on the usb-hdd). ](*,)

So, now I'm faced with 2 broken OS, I might as well just install Ubuntu on a regular hdd, and maybe not reinstall Windows at all :D

I'm still wondering though why Ubuntu did load from the ubs-hdd, but took 3mins for the blinking cursor.....

Best regards,
Clouds®

---

### Post by audiofreq on 2007-11-07
Mine does the exact same thing.

I changed my /etc/initramfs-tools/modules to look like this :

```
usb-storage
usbcore
usbhid
ehci-hcd
uhci-hcd
scsi_mod
sd_mod

```

but it's still the same.

Any ideas?

---

### Post by LinuxGuy1234 on 2007-11-07
> **Clouds® said:**
> Thanks for your reaction.
I have no idea what to do with the modprobe stuff (other than type modprobe usbcore in a terminal?) or how to regenerate the kernel.

However, I managed to destroy the Ubuntu installation when following a guide that aims to have Ubuntu load from an usb-hdd.

And then, when reinstalling Ubuntu to the usb-hdd again, I managed to destroy my Windows too (dunno why, afaik I used exact same procedure as first installation of Ubuntu, yet this time Grub was not placed on the usb-hdd). ](*,)

So, now I'm faced with 2 broken OS, I might as well just install Ubuntu on a regular hdd, and maybe not reinstall Windows at all :D

I'm still wondering though why Ubuntu did load from the ubs-hdd, but took 3mins for the blinking cursor.....

Best regards,
Clouds®

Do an:
```

sudo modprobe usb-storage
sudo modprobe usbcore
sudo modprobe usbhid
sudo modprobe ehci-hcd
sudo modprobe uhci-hcd
sudo modprobe scsi_mod
sudo modprobe sd_mod
sudo update-initramfs -u -k `uname -r`
```

after installing in order to have USB speed (little) fast.

---

### Post by LinuxGuy1234 on 2007-11-07
> **audiofreq said:**
> Mine does the exact same thing.

I changed my /etc/initramfs-tools/modules to look like this :

```
usb-storage
usbcore
usbhid
ehci-hcd
uhci-hcd
scsi_mod
sd_mod

```

but it's still the same.

Any ideas?

Renember to run:
```
sudo update-initramfs -u -k `uname -r`
```

---

### Post by audiofreq on 2007-11-07
Yeah I did.

Thanks though. I'll try again.

---

