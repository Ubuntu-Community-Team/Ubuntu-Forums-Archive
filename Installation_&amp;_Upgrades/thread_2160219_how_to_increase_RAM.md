---
title: "how to increase RAM ?"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2013-07-06
Hello  Ubunters :-)

What a silly question, eh? You only need find the suitable memory bar for your computer, stupid.
Well, the problem is I bought this slim computer a year ago or so. When I opened it the other day I found that the slot which is there to receive the memory bar is placed right under the CD/DVD drive!!!!:!:
So I my only hope is that there is perhaps a software I could use on a memory STICK and which could boost the ram ? 
Thanks in advance to anyone for help.

some technical features :

vendor: FOXCONN
      version: 1.0
      serial: To Be Filled By O.E.M.
      width: 32 bits
      capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
      configuration: boot=normal chassis=desktop cpus=2       uuid=7AB02C9C-1E00-1911-E7CE-D0278805B132
      *-core
      description: Motherboard
      product: TPS01
      vendor: FOXCONN
      physical id: 0
      version: 1.0
      serial: UL81035064864
      slot: To Be Filled By O.E.M.
      *-firmware
      description: BIOS
      vendor: American Megatrends Inc.
      physical id: 0
      version: 080015 (06/07/2010)
      size: 64KiB
      capacity: 960KiB
      capabilities: isa pci pnp apm upgradeshadowing cdboot bootselect       socketedrom edd int5printscreen int9keyboardint14serial       int17printer int10video acpi usb ls120boot zipboot       biosbootspecification
      *-cpu:0
      description: CPU
      **product: Intel(R) Atom(TM) CPU D525 @ 1.80GHz**
      vendor: Intel Corp.
      physical id: 4
      bus info: cpu@0
      version: 6.12.10
      serial: 0001-06CA-0000-0000-0000-0000
      slot: CPU 1
      **size: 1800MHz**
      **capacity: 1800MHz**
      width: 64 bits
      [B]clock: 200MHz 


[/B]

---

### Post by prodigy_ on 2013-07-06
> **christon74 said:**
> a software I could use on a memory STICK and which could boost the ram
It's called swap and Linux does support swap partitions and files. However, swap performance is always awful due to extra IO and low bandwidth. And you probably don't want to use any kind of flash memory for swap anyway because flash cells can only take a limited number of writes.

If the DVD drive is really blocking that memory slot, I'd suggest to remove it and seal the front panel with a sticker or something.

---

### Post by kostkon on 2013-07-06
> **prodigy_ said:**
> If the DVD drive is really blocking that memory slot, I'd suggest to remove it and seal the front panel with a sticker or something.
And buy a cheapo IDE/SATA enclosure and have it as an external usb dvd drive.

---

### Post by TNFrank on 2013-07-06
It sounds to me like you want to add more RAM to your computer. First you need to figure out if you have DDR1, 2 or 3 and how many pins your SODIMM is, 200, 204 or 240.  Then you need to find out how much RAM your system can actual handle.  My older NC78230 is a 32bit system and can only handle 2GB's of RAM. The newer 64bit systems can handle more. I have a 1GB Stick under the keyboard(internal) and a 1GB Stick under the pannel on the bottom of my laptop(external) so I'm maxed out at 2GB.  You should be able to find out info about your computer by searching on the Interweb. There should be a .pdf book somewhere that you can download. Good luck.

---

