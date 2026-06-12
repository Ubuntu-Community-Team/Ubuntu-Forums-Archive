---
title: "error: no such partition"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by x karloo x on 2010-03-21
Okay. I had Vista and Windows 7 running side by side, then I came across the new beta for Ubuntu. So I reinstalled Windows 7 over windows Vista (it was quite stubborn to remove) and deleted my other windows 7 partition. It booted fine. So then I installed Ubuntu from disk. 

I didn't really like Ubuntu, so I deleted the partitions. I had no idea it would cripple my system. Everytime I boot, it comes up 

error: no such partition
grub rescue>

I can't find any way to make this boot a cd, and I can't boot from CD in the bios, because no keys work... 

It used to say 'press F12 for boot menu' but now it doesn't.

What can I do?

I have a windows 7 installation disk. A Windows Vista Recovery Disk, and a Ubuntu Installation Disk.

Thanks.

---

### Post by rory526 on 2010-03-21
The grub bootloader was installed on the linux partition, so when you formatted that, you removed grub. When the computer boots it looks at the first few bytes on the first hard drive to find what to do next. These first few bytes are called the master boot record, or MBR for short. When you install linux, instructions are installed in the MBR tell the computer where to find grub instead of windows boot loader, but now grub's not there anymore.

It seems you want to write to the MBR, instructions to find your windows boot loader, so here are some methods I've found to do that:

1. If you have a DOS boot floppy, boot from it and use the command:

```
Fixmbr
```

more details here:

[http://www.astahost.com/info.php/Bootloader-Problem_t11250.html](http://www.astahost.com/info.php/Bootloader-Problem_t11250.html)


2. With a linux live CD you can follow the instructions on this webpage:

[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

Now, you say you're unable to boot to a live cd? Formatting your linux partition wouldn't have caused that. Can you enter setup to change your BIOS settings? (Usually F2 during boot-up)

If you can, then change your boot order to floppy first, then CD and then your hard drive(s).

I'm sorry to hear that you didn't like Ubuntu. Often people find it hard to get used to some of the slight differences in another os at first, but I'm certain that if you stuck at it for another little while, you will prefer it to windows.

Post again if you solve your problems or if yo need more help.

---

### Post by x karloo x on 2010-03-21
F2 was my bios settings. Now when I press it, my laptop just makes a beeping sound. I can't boot from anything other than my harddrive. 

Gahh, I'm so stupid. Obviously, as I can't boot from CD, and my laptop has no floppy, I'm pretty screwed.

What do you think could have messed my bios up? And can I fix it? 

Thanks for the reply

EDIT:  Nevermind, I have found a solution. I'm just going to buy a USB to SATA adaptor, reformat and install windows that way.

---

### Post by rory526 on 2010-03-21
It's very strange to me that removing an os would change the bios in any way. The beep produced after you press F2 or F12, is it a series of beeps, or just one?

If it is a series of beeps, this is an error code called a POST code and can help us find the problem.

Is your computer a laptop or a desktop? Have you added or changed any hardware on your computer recently?
I had a computer with an old power supply that wouldn't boot from a cd until I removed one of the hard drives. The power supply had too low a wattage to power them all.

If your BIOS is damaged, you can try flashing it or installing a new bios, but there is a small chance you can irrecoverably damage your computer doing this. Maybe this should be your last resort.

It's also possible to install linux to a usb key and boot from a usb key. If your computer is a desktop, maybe removing the hard drive will allow the bios to boot from the next boot device on it's boot list.

These are just some scattered ideas really. Sorry I can't do more. Tell us how you get on.

---

### Post by x karloo x on 2010-03-21
Thanks, the beep is produced once after each press of either F1 F2 F11 F12 or ESC. 

No hardware changes to my laptop at all. Except the partitioning of my harddrive. 

As I said in my edit, I'm going to buy a USB to SATA adapter, and try reinstalling windows that way. IMO it's a much better option that trying to flash my bios.

Thanks.

---

### Post by rory526 on 2010-03-21
Best of luck.

---

