---
title: "need help with sata_nv install"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by dragnrebrn1 on 2010-02-24
i need to figure out how to get karmic server installed on my computer.  for some reason the installation process is not finding my hard drive.  i have the sata mcp55 chipset which needs the sata_nv module from what i can tell.  its not loading it.

there is a point where it asks me if i have the driver on a usb stick.  i was wondering if anyone can point me to a tutorial or post that explains this.  or if there isnt one help me figure it out.

---

### Post by dragnrebrn1 on 2010-02-24
ok let me pose another question.  has anyone successfully installed karmic on a motherboard with the nvidia mcp55 chipset?

---

### Post by gordintoronto on 2010-02-24
What motherboard do you have?  "mcp55" does not define a chipset; several chipsets have mcp55.

---

### Post by dragnrebrn1 on 2010-02-25
im sorry i figured i knew what a chipset was lol.

it is an evga 680i 122-CK-NF68
the important part ( i think) of the lspci is :

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)

everything else seems to work ( havent tried audio b/c its going to be a server) but im thinking thats because the other things use different modules then the sata controller.



the full lspci is:
```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8400 GS] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

thanks for the reply =) 
Neil

---

### Post by gordintoronto on 2010-02-25
Yes, 680i is the chipset.

I found this review on Newegg: "Pros: I bought this board so I would be able to keep upgrading to newer components for a while, after reaching the limits of my previous system. I was surprised by just how many options the BIOS had. Everything works perfectly under Windows XP and Ubuntu 6.10, using BIOS p23. one of the best desktop boards available right now, period"

Other 2006/2007 reviews: "No hardware issues with linux at all," and "You want linux support this is the board."

Were this board and hard drive working previously, or have you made a hardware change?  Is it a RAID hard drive setup?  Has the BIOS ever been updated?

Is there any chance there is a loose cable?

---

### Post by dragnrebrn1 on 2010-02-27
it works with windows 7 and ubuntu 8.04 lts.  its just 9.04 and 9.10 that is does not work.  there is a section in the server install where it asks if i have any drivers on other media i just dont know how to get the right module and load it onto the usb stick.  is there any way to have the kernel load extra modules during instillation?  from what i have figured out its the sata_nv module i need i just dont think its loading.

---

### Post by gordintoronto on 2010-02-27
Open accessories/terminal, enter this command:
lsmod | grep sata

---

### Post by dragnrebrn1 on 2010-03-02
there is no output for lsmod | grep sata

```

~#lsmod | grep sata
~#

```

---

### Post by gordintoronto on 2010-03-02
Is it actually an IDE hard drive? I just noticed that lspci shows MCP55 as an "IDE interface."

I'm pretty much baffled at this point.

---

### Post by elect on 2010-03-03
> **dragnrebrn1 said:**
> i need to figure out how to get karmic server installed on my computer.  for some reason the installation process is not finding my hard drive. 

Same problem here, is it possible to load in such a way the module while running the live?


Its incredible, i can see it from nautilus, but i cannot from installation menu..

---

### Post by elect on 2010-03-03
Solved, it was enough choosing the alternate :p

cya

---

### Post by dragnrebrn1 on 2010-03-05
I ended up loading windows 7 64 and doing wubi.  it worked then i did modprobe -l *sata* and noticed sata_mv was the module.  i then loaded the live cd and it saw the hdd.  i then tried to install the server and everything worked.  i have not a clue why.  anyway thank everyone who helped.

-Neil

---

