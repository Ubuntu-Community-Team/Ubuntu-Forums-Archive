---
title: "New Install - Failed?"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by rocket neko on 2008-03-06
Booted from Ubuntu 7.10 LiveCD - everything seemed to work.

Installed to one of my HDDs. Installation seemed to go fine.

Shut down, fixed bios to boot from the Ubuntu drive.

Upon reboot, presented with the bootloader, Ubuntu at the top, followed by Ubuntu's diagnostic modes, then "other", then WinXP (dualbooting, obviously)

WinXP works fine, and is untouched by my monkeying around.

Ubuntu fails to boot up. The progress bar simply does not move from the far left.

Tried booting in recovery mode, it hung after what appears to be it loading drivers for this Microsoft basic optical mouse (how ironic).

Final message onscreen before it stopped doing anything read something like USB HID device driver. That's the ONLY USB HID device plugged in, so...


HELP! Did something go wrong during my install? How can I fix this?

---

### Post by Rohan sehgal on 2008-03-06
Dear sir,
Your system device or may be your USB HDD might have an IRQ conflict. To test this please chck is your usb hdd working on your system or not. If it is working try starting ubuntu without your USB HDD :(. If it does not, Try running ubuntu in a live cd and check if there are hardware conflicts.
Contact me on
[email]Rohan.upclose@gmail.com[/email]

---

### Post by rocket neko on 2008-03-06
So I went back and unplugged my mouse and tried to boot it into recovery mode again.
It stopped at about the same point and was still talking about USB, so I thought that since I have a tablet maybe it had meant that instead of the actual mouse and the tablet was causing problems, so I unplugged that as well and tried again.
This time it stopped at an area talking about partitions and my DVD drive. I was able to write most of it down.

"ide: failed opcode was: unknown" appeared about every three lines before this excerpt.
"Idm_validate_partition_table(): disk read failed
Dev hda: unable to read RDB block 0
unable to read partition table
Hdc: ATAPI 48x dvdrom dvd r ram cd r/rw drive 2048kb cache UDMA(33)
uniform CD ROM driver revision : 3.20"

After awhile, it popped up with this. . .

"ALERT! /dev/disk/by-uuid/0aaa203f-13d9-4398-a097-9d28a46ffcc0 does not exist. Dropping to a shell!"

At which point it gave me a command prompt that I didn't know how to use so I turned it off, decided maybe it was just a bug somewhere between downloading, burning, and installing, so I did all that again.

Upon reinstall it did not complain about my mouse or any other USB device (I did plug the mouse back in, though not the tablet yet.) The live CD worked fine, everything about install claimed to work fine, but upon trying to boot from the hard drive, I got the same error as the one quoted.

So, I'm out of ideas. Again, I am completely new to linux and the reason I downloaded this was to learn, so if anyone has ANYTHING that may help, as obvious as it may seem, please let me know.

---

### Post by froy02 on 2008-03-06
> Shut down, fixed bios to boot from the Ubuntu drive.


Try booting with the same bios set up that you had when you installed the ubuntu.  Do not change the bios setting.

---

### Post by rocket neko on 2008-03-06
So you want me to leave the BIOS booting from the CDrom before the HDD? that seems counter-productive.

---

### Post by rocket neko on 2008-03-06
> **Rohan sehgal said:**
> Dear sir,
Your system device or may be your USB HDD might have an IRQ conflict. To test this please chck is your usb hdd working on your system or not. If it is working try starting ubuntu without your USB HDD :(. If it does not, Try running ubuntu in a live cd and check if there are hardware conflicts.
Contact me on
[email]Rohan.upclose@gmail.com[/email]


I dont know how to look for hardware conflicts, but I did go in the live cd and look at the device manager (hoping that might help me find out how) and I noticed that it didnt seem to know that I had a dvd rom drive at all. Could this be a contributing factor? How do I tell it that the drive is there?

---

### Post by froy02 on 2008-03-06
It is not counter-productive.  It is normal for computers to have the CD-rom as first boot device since if there's no bootable cd in it it would boot to the next boot device which is usually the hard drive.  
You were not specific in your post what yoy meant by "fix the bios" so I assumed that you changed the boot order of your hard drives because like I said it is normal to set the CD-rom as the first boot frive and leave it there, my bad.

---

### Post by rocket neko on 2008-03-06
> **froy02 said:**
> Try booting with the same bios set up that you had when you installed the ubuntu.  Do not change the bios setting.

For the sake of nothing better to try, I did attempt to boot with the bios still booting from cd first. Nothing happened. Any other suggestions?

---

### Post by rocket neko on 2008-03-06
bump.

---

### Post by rocket neko on 2008-03-06
Ok, trying to provide as much information as I can.

I have two HDDs in my system. a 250GB SATA drive (with WinXP on it), and a 40GB IDE drive (trying to get Ubuntu on it).

I can boot from, and use, the LiveCD just fine. Everything seems to be working. When I install, I install it to the 40GB HDD, and it places the bootloader (GRUB?) there.

my BIOS is booting from this IDE HDD. I get to the bootloader just fine. If I choose WinXP from the list, it boots. No problems whatsoever. HOWEVER, Any Ubuntu option fails in the way I have described in a previous post.

From some poking around the web, there's a lot of problems with SATA and IDE drives being used in tandem. Is there a fix for this?

---

