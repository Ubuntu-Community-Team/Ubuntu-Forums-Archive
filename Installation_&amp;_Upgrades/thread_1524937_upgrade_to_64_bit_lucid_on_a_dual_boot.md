---
title: "upgrade to 64 bit lucid on a dual boot"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by jquis8411 on 2010-07-06
Hi I hope everyone is having a good night. Any way to my problem. I have the 32 bit lucid dual booted with win 7,  and I wanted to upgrade to the 64 bit lucid. I have the .iso on a jump drive ready to go, BIOS is set to boot from it, now it gets funny. Unless I misunderstand what grub does shouldn't my jump drive show up in the grub menu so that I can select it to boot from? My only options showing are 32 bit lucid and wins 7. It would be great if someone could help me out. TY

---

### Post by imondanet174 on 2010-07-06
Hello jquis8411
 
Acutally you should change your boot sequence in your BIOS to first boot from your USB device.
 
Your device will not show up in the existing grub boot menu.

---

### Post by efflandt on 2010-07-06
A live/install iso on USB created with Startup Disk Creator (and probably with Unetbooin) does not use grub (it uses syslinux to only boot that drive).  So if you are seeing such a grub menu, your computer is actually booting your internal hard drive.

Even if you set your BIOS to boot from USB, sometimes you have to press another key during the BIOS splash screen to boot from CD or USB, so you will not accidentally boot from something that may have something nasty on it.  The first and only virus I ever caught was a boot sector virus spread by floppy disks many years ago called Stoned Empire Monk (Monkey).  It would spread by booting from an infected floppy (even if accidentally from an unbootable disk that gave a "non-system disk" error).

Some other BIOS setting having to do with Legacy or Auto may also affect whether you can boot from USB.

A grub menu would normally only show when booting from USB if you did a full install (instead of just the iso) to USB, in which case you have to remember to put grub on the USB with the Advanced button.

---

### Post by jquis8411 on 2010-07-06
Thanks guys. I did have BIOS set to boot from USB. I just thought maybe it would show up in grub. But I'm all set now. Thanks again for the help.

---

### Post by vishnus on 2010-12-07
Hii! I have Win7 and Lucid 32bit installed. I want to upgrade it to 64bit Lucid without touching win7. How should i start with? I have the 64bit version in my USB (bootable).

---

