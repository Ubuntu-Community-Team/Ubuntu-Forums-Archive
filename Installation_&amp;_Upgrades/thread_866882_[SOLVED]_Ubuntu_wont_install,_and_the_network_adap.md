---
title: "[SOLVED] Ubuntu wont install, and the network adapter is not recognized in windows an"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by Hypnotics on 2008-07-22
Hey guys, I have a very frustrating problem here.

I'm trying to install Ubuntu 8.04, but to no avail.

I'm using a CD I burned the i386 iso on.
When I go "install", it loads the linux kernel, then shows the loading animation, and then this appears:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

And after a while, I start to get errors that look like this

```
[  203.832561] ata2.00: exception Emask 0x0 SAct....
[  203.832561] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00/a0 tag 0 pio 36
[  203.832561] ata2.00: status { DRDY }
WARNING: Synchronous SCSI scan failed without making any progress  
```

And it just keeps giving them.

Also, when I booted back into windows, it doesn't recognise my network adapter any more, and I can't connect to the internet.
I believe this is related to the problem above, as I don't think I touched anything else meanwhile.

I attached my system report made with everest if you need it.

Any help would be greatly appreciated.

Thanks!

---

### Post by chalewa on 2008-07-22
try to reinstall the driver in windows..

but an ubuntu install should not affect windows at all....




edit: also, check the integrity of your install disc

---

### Post by Hypnotics on 2008-07-22
> **chalewa said:**
> try to reinstall the driver in windows..

but an ubuntu install should not affect windows at all....

I tried to, but that didn't work either.

Checked the integrity as well, it says it's fine. Also did an MD5 checksum, everything OK there too.

Could it be related to the BIOS?

---

### Post by Pumalite on 2008-07-22
Maybe the card went south.

---

### Post by Hypnotics on 2008-07-22
> **Pumalite said:**
> Maybe the card went south.

Hope not.

Anyone else can help?

---

### Post by chalewa on 2008-07-22
what does 

```
lspci
```

```
lsusb
```


look like

---

### Post by Hypnotics on 2008-07-22
> **chalewa said:**
> what does 

```
lspci
```

```
lsusb
```


look like


Sory, where should I check those?

I tried eentering both commands in the prompt that appears but it says not found.

---

### Post by avtolle on 2008-07-22
The commands you were given to run should be run from the terminal, once Ubuntu is running; but you are being dumped into Busy Box before installation occurs. Can you boot from the Live CD (I presume that's the one you are using) and get into the terminal (Applications>>Accessories>>Terminal) to issue those commands and then post the output here?

---

### Post by Pumalite on 2008-07-22
Check if you have a connection with the Live CD.

---

### Post by avtolle on 2008-07-22
Take a look at this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for how to add boot options. I'd suggest you try all_generic_ide as a boot option, which is not discussed in the link, but which has been of help to some. It would be added to the boot line in the same manner as the example given in the link.

BTW, what wireless adapter are you using? If you know, you could post it (e.g., Atheros xxxx, Broadcom xxxx), and that might be helpful, too. That is what underlies the request to run lspci and lsusb made above (to take a look at what the system reports your wireless adapter, card or USB dongle, to be).

---

### Post by Hypnotics on 2008-07-22
> **avtolle said:**
> The commands you were given to run should be run from the terminal, once Ubuntu is running; but you are being dumped into Busy Box before installation occurs. Can you boot from the Live CD (I presume that's the one you are using) and get into the terminal (Applications>>Accessories>>Terminal) to issue those commands and then post the output here?

No, I get that Busy Box when I try to boot from the live CD too. 
I even installed wubi, and I still get it.

> **Pumalite said:**
> Check if you have a connection with the Live CD.

How do I do that?

---

### Post by Pumalite on 2008-07-22
Try Firefox

---

### Post by Hypnotics on 2008-07-22
> **avtolle said:**
> Take a look at this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for how to add boot options. I'd suggest you try all_generic_ide as a boot option, which is not discussed in the link, but which has been of help to some. It would be added to the boot line in the same manner as the example given in the link.

BTW, what wireless adapter are you using? If you know, you could post it (e.g., Atheros xxxx, Broadcom xxxx), and that might be helpful, too. That is what underlies the request to run lspci and lsusb made above (to take a look at what the system reports your wireless adapter, card or USB dongle, to be).\

Tried booting with the all_generic_ide, and I got in. Thank you!

Here's what the two commands output:

```
lspci

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)


lsusb

Bus 007 Device 002: ID 04cf:8819 Myson Century, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0951:1607 Kingston Technology 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by avtolle on 2008-07-22
> **Hypnotics said:**
> \

Tried booting with the all_generic_ide, and I got in. Thank you!
Glad it worked. Good luck.

---

### Post by Hypnotics on 2008-07-22
> **Pumalite said:**
> Try Firefox

Tried, and I don't have a connection

> **avtolle said:**
> Glad it worked. Good luck.

Thanks. I've edited the above post with the output of the two commands.

---

### Post by chalewa on 2008-07-22
you are running that lsusb command when you have the thing inserted right?


is this a usb network adapter?

---

### Post by Hypnotics on 2008-07-22
> **chalewa said:**
> you are running that lsusb command when you have the thing inserted right?


is this a usb network adapter?

I ran the command from the live CD.

I installed Ubuntu successfuly and it doesn't recognize the adapter either.

From what I can read from the drivers setup in windows, it is "REALTEK GbE & FE Ethernet PCI NIC"

---

### Post by Hypnotics on 2008-07-22
Could this be related to the BIOS btw? Is there something I should check there?

---

### Post by avtolle on 2008-07-22
I note that your wireless card (it is a card, correct?) is not showing up in the output from the lspci command, which, given your problem in Windows, too, makes me wonder if Pumalite was correct; it may have gone South, concurrent with the Ubuntu installation attempt. Wondering; can you open your computer to see whether it may have come loose?

EDIT: If it is usb wireless "dongle", again, has it come loose/out of the port somehow?

---

### Post by nascimento on 2008-07-22
STOP STOP STOP STOP!

Guuuuuys! It's obviously an hardware problem! but seems to be a easy-solved one.

IF, and only IF, you can hold yourself to do some "cleanning" on your hadware - do it like that:.

- Try to pull out all your pci-like boards
- get some SOFT RUBBER (that's right.. the pencil rubber)
- And "erase the bits" out of contact pins in the board(s)

This procedure will eliminate the oxidation...

A Network board or anything like that don't just vanish out from nowhere.

MUST be that one!

Ps:. try ONLY if you know what you're doing.. and pay attention to completly turn power off. (pull out the force cable - it's good)

ps2:. watch out to don't break garanties seals. if your's still uptime - don't get a headache and just change that one!

Hope it works...

---

### Post by chalewa on 2008-07-22
yea there is for sure something wrong with your actual hardware.

---

### Post by Hypnotics on 2008-07-22
Ok, thanks for the help everyone. I'll try to clean it up tomorrow and will give you an update on how it went.

---

### Post by Hypnotics on 2008-07-23
I just had to push it a little and now it works with no problems.

Thanks everyone for your assistance! You've all been of great help.

I love ubuntu alraedy!

---

### Post by chalewa on 2008-07-24
> **Hypnotics said:**
> I just had to push it a little and now it works with no problems.

Thanks everyone for your assistance! You've all been of great help.

I love ubuntu alraedy!

haha glad you got it working

---

