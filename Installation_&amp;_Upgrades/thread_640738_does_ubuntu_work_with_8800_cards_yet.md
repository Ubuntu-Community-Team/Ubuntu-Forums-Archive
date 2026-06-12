---
title: "does ubuntu work with 8800 cards yet?"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by garylouden on 2007-12-14
just wondering as ive tried installing ubuntu over the pas year or so and it never works.

any idea if the new release will work with my 8800GTS?

---

### Post by rsambuca on 2007-12-14
Yes, but you need to install the nvidia beta drivers manually.

---

### Post by garylouden on 2007-12-14
any chance of how to do this. im new to linux so dont know how to do much more than install the OS

---

### Post by ericartman on 2007-12-14
I have been running an 8800 gts since I first started with Feisty. It works the same on Gutsy. I get a icon for the restriced driver in the top right corner and click on it, check the option for the  nvidia driver(restricted), and let it install and do the restart)  and its done. What problems have you been having? I quite honestly never had one with this board.


Cart.

---

### Post by garylouden on 2007-12-14
wierd when i go to install ubuntu i get to the screen to select install then it goes black and does nothing. i thought it was my 8800 but maybe not :S

---

### Post by rsambuca on 2007-12-14
It is pretty hit and miss with the 8800's.  My suggestion is to use the Alternate Cd to install, and then add the drivers later.

---

### Post by mellowd on 2007-12-14
Use Envy to install the drivers. I had Mint working with my 8800GT no problem

---

### Post by ericartman on 2007-12-15
I've had this happen on 64 bit  versions, I got around this by burning as slow as possible and using different burners and media finally got one to work, also it doesn't happen as much with a i386 version for my system. Alternate versions seem to work better for me as well. Mint worked nicely. Good luck

Cart

---

### Post by garylouden on 2007-12-15
yes 32bit seems to work for some reason but the proble with that is that my Creative X-FI card only has 64bit drivers available.

anyone know if there is any way of getting sound from 32bit with an XFI?

---

### Post by p_ano on 2007-12-15
no luck with my 8800 gts.

tried in all sorts of combinations -> 

- enabling restricted drivers
- install nvidia 100.14.23 driver thru nvidia-installer
- install drivers thru Envy script
- compile latest kernel
- play with apic,lapic,noapic,acpi=off and other kernel options
- installed 7.10 and 7.04, same issue with both
- updated bios
- all sorts of xorg.conf settings and tweaks
- disabled acpi in bios

the only key to my issue is this msg ->

[   20.393275] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   20.480120] PCI: Failed to allocate mem resource #3:2000000@fe000000 for 0000:05:00.0 (this is the address of my video card)

i would say this is a motherboard issue, but my 7600 GT worked just fine with the same motherboard.

i've read about a billion threads and see the same replies over and over.   none of these are working for me.  ubuntu was awesome with my 7600 GT, but now it's useless with my 8800 GTS.   i can use the "nv" or "vesa" drivers, but they're so slow i can hardly bear it.

until ubuntu gets problems like this resolved it will never be ready for the prime-time.

---

### Post by rsambuca on 2007-12-15
> **p_ano said:**
> no luck with my 8800 gts.

tried in all sorts of combinations -> 

- enabling restricted drivers
- install nvidia 100.14.23 driver thru nvidia-installer
- install drivers thru Envy script
- compile latest kernel
- play with apic,lapic,noapic,acpi=off and other kernel options
- installed 7.10 and 7.04, same issue with both
- updated bios
- all sorts of xorg.conf settings and tweaks
- disabled acpi in bios

the only key to my issue is this msg ->

[   20.393275] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   20.480120] PCI: Failed to allocate mem resource #3:2000000@fe000000 for 0000:05:00.0 (this is the address of my video card)

i would say this is a motherboard issue, but my 7600 GT worked just fine with the same motherboard.

i've read about a billion threads and see the same replies over and over.   none of these are working for me.  ubuntu was awesome with my 7600 GT, but now it's useless with my 8800 GTS.   i can use the "nv" or "vesa" drivers, but they're so slow i can hardly bear it.

until ubuntu gets problems like this resolved it will never be ready for the prime-time.
Not Ubuntu's fault here!  Unfortunately using the newest hardware is often not a good combination for easy linux use.

---

### Post by mellowd on 2007-12-15
> **p_ano said:**
> 
until ubuntu gets problems like this resolved it will never be ready for the prime-time.

Not really, There is only 1 old driver for my 880GT on windows xp. I'm currently using a beta driver for performance. 

It really should work, I'm not sure why it's not working. There might be a compatibility issue with linux, your motherboard and video card altogether.

My 8800GT was easily installed in Linux and it's even never than the 8800GTS

---

### Post by Rupertronco on 2007-12-15
> **mellowd said:**
> Not really, There is only 1 old driver for my 880GT on windows xp. I'm currently using a beta driver for performance. 

It really should work, I'm not sure why it's not working. There might be a compatibility issue with linux, your motherboard and video card altogether.

My 8800GT was easily installed in Linux and it's even never than the 8800GTS

It depends on what GTS he has. New ones were released about a week ago (G92 core).

---

### Post by mellowd on 2007-12-15
> **Rupertronco said:**
> It depends on what GTS he has. New ones were released about a week ago (G92 core).

True, though he doesn't mention if he has the new one

---

### Post by Mike'sHardLinux on 2007-12-15
You people with the 8800 GTS who have it working ok, would you mind telling us the specific model(s) you have? I have been wanting to get one but the possibility of problems in Linux has held me back.

Thanks!

---

### Post by p_ano on 2007-12-16
i have a G80 GTS, so it's definitely supported by the drivers.    it's a memory allocation issue of some sort.   i tend to agree with mellowd that this a compatibility issue with the 8800gts + nforce4 + ubuntu.

can any gurus here decipher the memory error? ->

[ 20.393275] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[ 20.480120] PCI: Failed to allocate mem resource #3:2000000@fe000000 for 0000:05:00.0 (this is the address of my video card)

---

### Post by Trampis on 2007-12-20
My 8800 works ok with the exception of the restricted drivers, I used envey to install drivers but in order to get direct 3D to work I have to use the restricted drivers and when i go to the restricted drivers menu it reads "your system does not need any restricted drivers" do i need to run it as root or is something wrong?

---

### Post by KimoSaber on 2007-12-21
I got my computer (partly) to work with the 8800 GTS 512 (G92 core) card. I used the Ubuntu 7.04 Live CD and installed in the safe graphics mode. I kept getting an error while installing. Retried second time and was able to install from the Live CD.

I didn't install the latest Nvidia drivers. However, today  when I booted my computer I got the same hardware error while installing. Booted a second time and was able to boot up to the Ubuntu desktop. I have updated Ubuntu with the latest updates. Everything works except the bootup error and no 3d effects. It is running pretty fast, not sluggish at all.

Will have to wait for the upgrade or patch.:(

---

### Post by Trampis on 2007-12-21
you're 3D effects don't work either? is there a fix for this that anyone knows?

---

### Post by KimoSaber on 2007-12-21
Trampis, I haven't tested the 3D effects. I didn't want to mess up the install. I haven't tired it with the generic VESA driver. I didn't think it would work.

I fixed the bootup error. I deleted the "no Splash" on the menu.lst.

---

### Post by notaphish on 2008-01-16
I have a 8800GT Superclock with the new core and I had some troubles with the live cd.

The way that I got the live cd to boot was by running it with 'vga' changed to '800x600' and then installing the nvidia driver with envy (like the previous poster mentioned). 

note: I did try to install the driver via the script on nvidia's website but it wouldn't work after reboot so I was lazy and just had nvidia install it manually which worked fine after reboot.

OpenGL games like WoW work fine with the card but like was mentioned earlier there is incredibllly-low fps in direct3d games from what I have seen so far.

---

