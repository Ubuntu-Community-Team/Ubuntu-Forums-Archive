---
title: "Install to external USB 2.0 hard drive?"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by irrdev on 2008-11-16
Is it possible to install Ubuntu to an external usb hard drive, and have the BIOS boot from the external hard drive at startup, assuming that the hard drive is plugged in? I know that the BIOS can detect and boot from USB flash drives, but are external hard drives also supported? If it is possible, how does Ubuntu handle working from an external drive? 

Thanks in advance for any help on this matter.

---

### Post by mlentink on 2008-11-16
Entirely possible, in fact this is the way I try out new releases.
Your pc should be able to boot form a usb-drive, but most modern systems are.
Boot up from your Live-CD with the usb-drive plugged in. Make sure at prtition time to specify the usb-drive, and use the 'Advanced'- button to specify you want to install GRUB on the external drive (usually hd1). Rebooting to your usb-drive will not work (yet) as GRUB will look for the internal drive. So boot up with the Live-CD again, and edit the /boot/grub/menu.lst file ON THE USB-DRIVE. Change the *references* to the OSs installed on the internal drive from hd0 to hd1, and the ones on the usb-drive to hd0 respectively. If you don´ t want to mess with your internal drive at all, you can even delete those references.
Now you can reboot, make sure you reboot to the usb-drive.

Good luck, and have fun!

---

