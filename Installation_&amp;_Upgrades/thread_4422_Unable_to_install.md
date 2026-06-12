---
title: "Unable to install"
date: 2004-11-15
forum: Installation &amp; Upgrades
---

### Post by cacofonix on 2004-11-15
I got myself a new computer and the worst thing has happened :cries: I cant install linux :'( every distrobution has troubles Mandrake cant find the cdrom after booting suse has corrupted video gentoo takes too long which leads me to ubuntu, ubuntu keeps telling me I have to specify raid or something which is weird cos I dont have raid at all I also have the option of selecting LVM which I dont understand but when I selevt them both I get error messages saying that it cant find partions or that they are all full up.

My specs are:
p4 2.8 ghz
optorite dvd burner
intel grantsdale 915p
Intel IDE controller 82801fb Ultra ATA storage controllers-2651

---

### Post by Marauder1 on 2004-11-15
Are you dual booting on the system
or is it an install from a fresh hard drive ???
Maybe you have to set your first primary
partition as bootable or active ???
Maybe an option in your bios that affect your drive ???
Else i dont know never seen that before.

Keep it up i'm sure its only a few details .

---

### Post by wallijonn on 2004-11-15
Is it a SATA or IDE drive. If it is IDE, make sure that in the BIOS you have set the HD subsystem to Legacy, PATA only (no PATA+SATA). If it is SATA, then make sure that PATA is not enabled.

---

### Post by cacofonix on 2004-11-19
I tried disabling PATA but then the cd drive wouldnt work anymore I then tried every other variation and that never wokred so I dont know what else to do, please help me Im hating not having linux to use I need my linux fix. :-(


cacofonix

---

### Post by az on 2004-11-19
I think that the hoary installer is the new one based on debian sarge rc2.  It is supposed to handle much more hardware.  Try that, perhaps?

---

### Post by cacofonix on 2004-11-19
thanks for the help azz :D is there a Hoary iso image available?


cacofonix

---

### Post by jdong on 2004-11-19
From the installer, ALT+F2 should let you spawn a console.
 Output [b]lspci
  dmesg | grep ide
 dmesg | grep hd
 [/b]

---

### Post by cacofonix on 2004-11-19
Thanks for the help jdong

```

# lspci
/bin/sh: lspci not found

```

```

# dmesg | grep ide
ide: Assuming 33mhz system bus speed for PIO modes; overide with idebus=xx
ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: Ports already in use skipping probe
ide1: at 0x170-0x177, 0x376 on IRQ 15

```

```

# dmesg | grep hd
hdc: OPTORITE RW DD0405, ATAPI CD/DVD-ROM drive
hdc: ATAPI 40x DVD-ROM DVD-R CD-R/RW drive 2048 KB cache

``` 

if Im reading this correctly it looks to me like it cant find my hard drive.

cacofonix

---

### Post by jdong on 2004-11-19
You are correct. From this output, it seems like the Ubuntu kernels are not detecting your hard drive. Very strange... Hoary installer probably won't help you out here. The PIIX chipset is one of the best supported Linux IDE chipsets... there's no excuse.
 
 
 Let's diagnose this problem a bit...
 
 First off, are you SURE that you BIOS is seeing this hard drive? Is it connected properly and such (check the ends of the IDE cable, etc)

---

### Post by cacofonix on 2004-11-20
Im not sure if the BIOS is able to see the drive Windows runs perfectly suse installs without a problem mandrake cant find the cdrom and gentoo as far as I can tell doesnt have a problem either (never completed install got bored). Would Windows work ok if the cable wasnt connected properly?


cacofonix

---

### Post by cacofonix on 2004-11-20
I checked if the BIOS is able to find the HDD and it seems to be able to find it I enabled all of them (PATA SATA) and turned on LBA and I am now able to install Mandrake without a problem but I still have trouble with ubuntu :( 

BIOS settings
On Chip SATA Mode [Enhanced]
xPATA IDE Set To CH.0 Master/Slave
SATA Port 0/2 Set to CH.2 Master/Slave
SATA Port 1/3 Set to CH.3 Master/Slave

```

# dmesg | grep hd
ide0: BM-DMA at 0fx000-0f007, BIOS Settings :hda: DMA hdb: pio
ide1: BM-DMA at 0fx008-0f00f, BIOS Settings :hdc: pio hdd: pio
hda: ATAPI 40x DVD-ROM DVD-R CD-R/RW drive 2048 KB cache UDMA (33)

```


cacofonix

---

### Post by cacofonix on 2004-11-22
Do any of you guys have a clue as to how I can fix this?  :-k

---

### Post by bcp627 on 2004-11-24
The live cd runs fine for me, but I can't find the installer.  Perhaps they should take a page from the Mepis playbook and have an installation center icon.

On a positive note, Ubuntu recognizes the Broadcomm chipset on my wireless pcmia card(which Mepis does not do).  When I get my router in the mail, hopefully I'll be up and surfing the internet on a wireless connection in very short order.

---

### Post by malin on 2005-02-11
I have the same problem with SATA hard drive and ide cdrom. I've tryed new hoary beta and nothing changed. So it's kinda sucks. Fedora 3 works and sees both drives, so it could be fixed. Any new ideas?

---

### Post by nathan_kerr on 2005-02-12
I too seem to be having a similar problem trying to install Ubuntu onto SATA hardrives. I get about half-way through the installation to the part where it tries to install the GRUB boot loader. There it hangs at the 50% and never moves again (I left it for an hour). Any idea on what to do to fix this (play around with the BIOS maybe....).?

---

### Post by malin on 2005-02-12
Well, I should have been reading more carefully, there is even [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440) for that. I read all the comments but still can't find solution. It looks like SATA driver grabs ports required for ide devices. I hope someone will fix this before Hoary release…

---

