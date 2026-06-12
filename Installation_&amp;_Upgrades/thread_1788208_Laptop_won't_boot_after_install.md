---
title: "Laptop won't boot after install"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by papillion on 2011-06-22
I've been running Ubuntu on my Acer 5100 laptop for about a year and a half. The latest version I had was 10.10 when my disk crashed and burned and had to be replaced. This was an external hard drive as my internal one died long ago and I'm too lazy to replace it.

So things were fine until the crash.

Bought a new hard drive today (same brand and model as the one the system was installed on before), downloaded 10.10 and installation goes fine. Then, in the end, I am told 'you need to reboot in order to use your new system'. So I say yes and the system ejects the CD-ROM and starts the shutdown process. Then it gets to doing something with the CD-ROM (/sr0) and it gets an IO error. Of course this is because the thing was ejected! So I get this loooong list of IO errors (all the same) on device sr0 and I have to manually reboot the system by the power button.

The system starts to come up, I see the BIOS hit the external drive, and nothing. It sits there with a blinking cursor at the top left of the screen and does nothing. 

Now, I've looked at a few things:

1: I've made sure the external drive is the first boot device.

2. I've made sure the disk was actually good and not damaged.

3. I've made sure the ISO I downloaded has the same hash as the one I got

I've even tried the install on ANOTHER drive and the same thing happens!  I know 10.10 can run on this system as it HAS in the past with no problems at all.

Can anyone tell me what might be going on?

Thanks!
Anthony :(

---

### Post by dino99 on 2011-06-22
sr0 refer to the usb of that hdd (not recognized)

[http://support.acer.com/acerpanam/server/0000/Acer/AltosG710/AltosG710faq13.shtml](http://support.acer.com/acerpanam/server/0000/Acer/AltosG710/AltosG710faq13.shtml)

---

### Post by papillion on 2011-06-22
[QUOTE=dino99;10967526]sr0 refer to the usb of that hdd (not recognized)

Hi Dino99:

Thanks for the reply but I don't think that applies to the problem I'm experiencing. Installing Ubuntu *makes* the drive bootable and I shouldn't have to make it bootable before Ubutnu wipes it clean and installs. The tutorial you referenced seems to be specific to making it Windows bootable which I am not doing.

Besides, these drives have worked before. No reason why they would stop working ONLY on boot on this computer. I could even buy a damaged boot sector if it weren't happening on all three drives.

Any other ideas?

---

### Post by dino99 on 2011-06-22
ok maybe i've answered too quickly, sorry :(

what recovery mode does when booting ? (hold "shift" key down at bios end process, to see the grub menu)
you can then try "repair packages"

other tweaks: on the booting line, edit it (E) and add either:
noacpi, nolapic, noapic, nomodeset, irqpoll, pci=nobios, acpi=force

then if one of them works, add it to grub (sudo gedit /etc/default/grub) and finally: sudo update-grub

---

### Post by papillion on 2011-06-22
> **dino99 said:**
> ok maybe i've answered too quickly, sorry :(

what recovery mode does when booting ? (hold "shift" key down at bios end process, to see the grub menu)
you can then try "repair packages"

I've not tried recovery mode yet as I didn't think the system was even getting to the bootloader. But I'll try in the morning and see what happens. This is really strange since these are new drives and one that WAS working before (and IS working on another computer). Thanks for the grub pointer though, I'll try it.

Anthony

---

