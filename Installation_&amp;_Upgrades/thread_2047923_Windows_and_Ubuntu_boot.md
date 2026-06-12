---
title: "Windows and Ubuntu boot"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by natomyeggo on 2012-08-25
I currently have the latest version of Ubuntu (12.04 I think.) I just bought a new computer with the hopes of a awesome dual boot. Windows 7 was preinstalled with no discs and I wanted to have Ubuntu. When I finished installing Ubuntu, windows started to have problems and had to do self checks. It then got to a point where I couldn't boot into Windows, so I wiped the harddrive and started with ubuntu. I now have a copy of windows from a friend on a USB stick. I took the windows 7 iso and used unetbootin to put it on the USB. I restarted and nothing happened. Then I went into the boot settings for my HP and selected the USB. Booted into GNU GRUB with the following options available, none of witch are Windows 7 ( "{}" is used as separation): 
Ubuntu. with Linux 3.2.0-39-generic-pae{} 
Ubuntu. with Linux 3.2.0-39-generic-pae (recovery mode){}
 Previous Linux Version{}
Memory Test (memtest86+){} 
Memory Test (memtest86+, serial console xxxxxxxxxx) dont know if that is incriminating or not.
 

Should I just remove everything and install windows, then Ubuntu or what?
Thanks for the help.

---

### Post by Laiquendi on 2012-08-25
I've run up a couple of times into Win7 not booting from USB, I do not know the source though.

If I were you I would install Win7 and then Ubuntu, since it's always working (as far as I've heard). Only try not to overwrite Windows with Ubuntu :P

---

### Post by Mark Phelps on 2012-08-27
> **natomyeggo said:**
> I currently have the latest version of Ubuntu (12.04 I think.) I just bought a new computer with the hopes of a awesome dual boot. Windows 7 was preinstalled with no discs and I wanted to have Ubuntu. When I finished installing Ubuntu, windows started to have problems and had to do self checks. It then got to a point where I couldn't boot into Windows,
Did you use the "alongside" option that used a slider to shrink the Win7 install? If so, you encountered the common problem where that ends up corrupting the Win7 file system, rendering it unbootable.  IF you had come here first asking about HOW to do this, we could have advised you so this would not have happened.

>  so I wiped the harddrive and started with ubuntu. I now have a copy of windows from a friend on a USB stick. I took the windows 7 iso and used unetbootin to put it on the USB. I restarted and nothing happened.
Microsoft has its own Win7 USB creator -- which must be run from Windows.  You will need the Windows ISO file and a working Win7 PC to do this.

>  Then I went into the boot settings for my HP and selected the USB. Booted into GNU GRUB with the following options available, none of witch are Windows 7 ( "{}" is used as s ... 
Unetbootin is used to create LINUX boot CDs/USBs, not Windows -- which is why you saw no Windows entries when you booted from it.  See comments above about creating Win7 boot USB.

> Should I just remove everything and install windows, then Ubuntu or what?
Thanks for the help.
Easier to install Windows first -- because Linux distros can find them and create boot menu entries for them with ease -- which is NOT true when you install Linux first, then MS Windows.

---

