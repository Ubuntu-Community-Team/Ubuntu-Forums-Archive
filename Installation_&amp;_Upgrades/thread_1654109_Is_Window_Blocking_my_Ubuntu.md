---
title: "Is Window Blocking my Ubuntu?"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by abanta11 on 2010-12-27
So, I've just suffered a virus on my last laptop and promptly replaced it after 2 years with a netbook. I'll get that running again, but that's a separate issue. Starting all over again makes you appreciated how annoying and fragile Windows can be.

Problem: After downloading Ubuntu 10.10 from ubuntu.com, following all USB Booting instructions, I was able to trial run Ubuntu late last night once I saved the boot order to use the USB drive first. Things worked fine, and I was pleasantly surprised by how nice everything works... so far.

After shutting down, the boot order must have been erased. No amount of F-Keys or other buttons allows me to enter Setup to reboot Ubuntu from USB. All I get is a screen saying "Choose your OS" with one option: Windows 7 (Starter). EVERY key takes me to this same screen at startup, otherwise it just boots Windows 7.


Advice? Is it worth using Wubi if I just plan on keeping Windows and installing Ubuntu side by side anyways? 


Thanks much;)

---

### Post by wilee-nilee on 2010-12-27
Do you know the actual per-session boot menu key prompt for your computer. This is a boot from menu outside the bios.

Tell me the computer model an I will look it up on Goggle, it might even be the esc key

---

### Post by Bucky Ball on 2010-12-27
Dual boot. Make sure you have some free space (or unwanted partition) on your hard drive and install Ubuntu from the running USB version. There should be an icon on that desktop 'install Ubuntu'. 

When you get to partitioning, choose to manually partition. You will see the Windows 7 partition there (should be NTFS format). Just leave that alone and install Ubuntu to the free space/partition.

This should re-write the grub and you should have all OSs available at boot.

A couple of things: 

1/ 10.10 is not an LTS release (long term support) and as such is supported for two years. 10.04 *is* LTS and is supported for three.

2/ Ubuntu Netbook Remix (now called Ubuntu Netbook Edition I think) is another neat option. Runs great and is designed specifically for the netbook environment.

Good luck with it. A dual-boot install will run faster than off the USB dongle.

---

### Post by abanta11 on 2010-12-27
ASUS Eee PC 1001P-PU17-WT
Intel Atom N450, 32-bit

I swear that I've tried the Esc key, and every other option. Thanks for both help

---

### Post by wilee-nilee on 2010-12-27
> **abanta11 said:**
> ASUS Eee PC 1001P-PU17-WT
Intel Atom N450, 32-bit

I swear that I've tried the Esc key, and every other option. Thanks for both help

So it is the esc key. If you loaded the thumb with Unetbootin I notice that it will not show the thumb on the next boot, even on the per-session boot menu.

So you have probably unplugged the thumb and booted it to W7 then plugged it in to see if it shows. Reboot it and it should show up with the esc key prompt. Unplugging and plugging again I think is what it needs, I suspect since many change the bios that there is a script so that it doesn't read the usb after running so the computer goes to the bootloader.

Edit you might look in the bios if the esc key isn't bringing up the menu for a on off for the esc key prompt. With my acer one d250 netbook it is f12 and has a on off in the bios.

---

