---
title: "ubuntu studio hardy install problems"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by keeanrunt on 2008-08-03
the main thing i need to know is ow to find my howst name. and not knowing much about that the only place i saw it was when im trying to install ubuntu studio 8.04 hardy.  so is there a way to find out this "host name" in win xp and apparently if u dont have the host name and try and install ubuntustudio anyway it can't log in, well for me anyways.

---

### Post by dileepm on 2008-08-04
> **keeanrunt said:**
> the main thing i need to know is ow to find my howst name. and not knowing much about that the only place i saw it was when im trying to install ubuntu studio 8.04 hardy.  so is there a way to find out this "host name" in win xp and apparently if u dont have the host name and try and install ubuntustudio anyway it can't log in, well for me anyways.
Try "who" command without quotes of course :-)

---

### Post by Sangdrax on 2008-08-04
I too have install problems with my Ubuntu. I have a Kohjinsha SC3WP06GA. I installed Ubuntu 8.04 Hardy using an USB with a LiveCD in it (created using Unetbootin from Vista). 

1-I installed Ubuntu after loading the ide-generic, ide-disk, ide-core modules before install. If not, I cannot see the hard drive where I want to install. 

2-The install goes OK, with sound, bluetooth, NO network. After install and reboot, just after GRUB (where you choose what you want to boot) after selecting Kernel-Generic, the screen turns black with the cursor on the upper left corner waiting... 

I tried: 

a)-Booting options: pci=noacpi, pnpbios=off. It doesn't work. it behave the same way. :mad:

b) Re-install GRUB, find /boot/grub/, root..., setup... update-grub, and so on. Result: no boot. 

c) recreate initrd.img with mkinitramfs modifying /etc/modules (adding ide-generic, ide-core, ide-disk). The same, doesn't boot. 

Note: in the LiveCD from Ubuntu Hardy (8.04) there's an option to install next to the windows partition. I did it and the Windows Vista Boot Manager recognized it, there was a second system "Ubuntu" which did not boot. 

I said that the network doesn't work, in Ifconfig there's only the "loop" device. Anyone know the module for the Realtek Ethernet Card Model ?

(Yes, I am a little newbie with Linux)

Thanks for your help, I a little despserate with this... :(

---

