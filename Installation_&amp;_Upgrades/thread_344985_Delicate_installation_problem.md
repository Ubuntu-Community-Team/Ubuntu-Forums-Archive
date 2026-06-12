---
title: "Delicate installation problem"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by RythmDivine on 2007-01-23
Hello, this is my first post here. I have now decided to get rid of my windows install once and for all. However...

**Situation**

I have a Intel P4 2,8GHz sitting on an Asus P4P800 MoBo. I cannot install Edgy.

I have done a memtest
i have checked the (Official) CD
I do have a running windows XP on the computer.

**What happens**

I reboot with the CD in the only optical drive, i get to the starting screen where i can choose different options. It loads the linux kernel OK. I see the Ubuntu loading screen (the one with the running bar below). But then one of three things happens:

1) it says 

[17179765.508000) hdd: cdrom_pc_intr: drive appears confused (ireason = 0x)
IRQ 169: Nobody cares
Handlers: ide_intr +0x0/0x1f0
ata_interrupt +0x0/0x140(Libatal)
usb_hcd_irq +0x0/0x60(USBcore)
(try booting with the "irqpoll" option)

several repeats of this, then it just sits there waiting.

2) 

[17179786.936000] BUG: soft lockup detected on cpu#0!

then it just sits there waiting.

3) it just sits there waiting.

Now, i read several posts on the forum wich suggest that i change the BIOS setting for onboard IDE operate mode to Compatible instead of enhanced. But this way BIOS doesnt detect my DVD-drive and 2 of the 6 harddiscs. so i cant boot and get into the ubuntu disc.

Also, trying to boot with the irqpoll-option just gets me to problem 2 or 3 again.

I have tried an old knoppix CD, but that one halts also due to a irq 18 problem. I have also tried a ubuntu dapper CD i borrowed from a friend, this cd once worked back in august when i first tested ubuntu for a couple of days, but now i get the same error messages as above. The only machine-wise alteration that i have done since august is new mouse and keyboard, and adding two HDDs.

Im at a loss as what to try next. any ideas are welcome.

---

### Post by wpshooter on 2007-01-23
When you say you "checked the official CD", do you mean that you checked the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Other than that, if it were me, I would consider taking about 4 hard drives out of the machine.

---

### Post by kebes on 2007-01-23
Looks like you've already tried alot of different things. Here are some random ideas that spring to mind:

If you have any USB devices plugged in, try unplugging them before booting. See if that works. If you have USB mouse and/or keyboard, try switching to PS2 inputs for the installation. (You'll probably be able to switch back to using your USB devices once the install is finished.)

Also if the "irqpoll" option changes what stage you get to before the lockup, then that's a good thing. Try with and without that option... you can also try other combinations of kernel flags like "all-generic-ide" which might help.

---

### Post by RythmDivine on 2007-01-24
Hi and thanks for the answers.

Yes, i mean checking the cd for integrity via the built-in tool.

I did another try now, systematicly disconnecting all USB-devices except for the keyboard. Also systimatically disconnecting all HDDS. and always with the irqpoll-option. Sad to say that even without any HDDs and only a single USB-device, i still get errors:

[17179713.052000] BUG: soft lockup detected on CPU#0!

Any other ideas?

Edit: after reading some more on this issue, it seems that this is a kernel bug and has been around since october, and that there is no working solution or work-around. this only leaves me with the option of re-installing windows XP, since i need that computer and cant afford to wait for the next release of ubuntu (wich hopefully has a solution!).

---

### Post by RythmDivine on 2007-02-02
Ok, now i tried with an old 6.06 Dapper CD, and tha very same thing happens! So this cannot be related to current kernel. After this i tried Edgy again, this time with telling BIOS that the OS is NOT PnP. This leaves it hanging at the ubuntuscreen with the counter below the logo.

Anyone got more ideas?

---

### Post by kebes on 2007-02-02
You could try running the development version of Ubuntu (Feisty Fawn). The daily snapshots can be downloaded here:
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

Note that this version of Ubuntu is "experimental" and thus might not be stable. However if it is able to boot and install, then this will give you some new hints and options. In particular, if you can boot the LiveCD, you could use that environment to install Edgy, and upgrade Edgy's kernel. Then (hopefully) the new Edgy install will work fine.

It may also be possible to install Feisty and then downgrade to Edgy.

If Feisty boots properly, then it's possible that this is a kernel issue that is fixed in the latest kernel. Note that as of now, Fedora Core 6 and OpenSUSE ship with a newer kernel than Ubuntu Edgy. Thus you could try installing one of those, instead.


I know this is frustrating. Hope something works soon...

---

### Post by RythmDivine on 2007-02-02
After much testing and searching different Linux-forums i found a

**Solution**

In BIOS settings, Keep the Enhanced mode but change drive type to SATA Only. This made the BIOS still able to find my 4 PATA drives (including the DVD) and succesfully boot and install!

so, it was a BIOS issue after all. Hope this helps pthers with the same motherboard...

---

### Post by kebes on 2007-02-02
Thanks for posting back with a solution! I added your install hints to the Ubuntu Hardware wiki ([Motherboard section]("https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards")). You can find the info I added here:

[https://wiki.ubuntu.com/Asus_P4P800](https://wiki.ubuntu.com/Asus_P4P800)

You can add/edit if I made a mistake...

---

