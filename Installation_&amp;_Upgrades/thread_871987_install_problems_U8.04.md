---
title: "install problems U8.04"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by bfuzze on 2008-07-27
Installation problems on new desktop using Ubuntu 8.04 Live CD.  Initial screen loads ('Try Ubunto...', 'Install Ubuntu...', etc.), but after selecting either of the first 2 options the kernel loads and then the system freezes with blinking cursor in upper left corner.  I tried removing boot options and could see the initialization and it always stops after 
> io scheduler cfq registered (default)
I googled this and all related posts suggested using the standard optional parameters: noapic acpi=off nolapic which I tried, but had no effect.  

I'm new to Ubuntu, but need to get it working asap.  I have some experience debugging within Ubuntu, but not installation so I don't even know how to find the error.  

I should note that I was able to successfully install Ubuntu on this machine earlier as first os, but then when trying to setup Windows, the Windows XP installer would not recognize the partitions or even the entire drive (the latter because apparently the prior to SP2 XP can't recognize drives over a certain size).  So I decided to try to install Windows first, then Ubuntu.  This tells me this might be related to the partitioning, again, except this time on the Ubuntu side (even though I made sure the Windows installer left the unpartitioned space as free (unformatted) space).  I'd be fine with wiping the 
Windows install, but I can't even get to the Ubuntu desktop.

I also tried reconfiguring hardware components via BIOS, but if it installed before...

I'm out of ideas and could really use some assistance or perhaps just the best way to format the drive, but that would be a last resort.

TIA

---

### Post by Pumalite on 2008-07-27
Did you try 'Safe Graphics'?

---

### Post by bfuzze on 2008-07-27
I tried selecting safe graphics mode from the popup on the initial screen, no change.
I also tried selecting the safe graphics mode and adding noapic acpi=off nolapic to the boot options command line, still freezes at the same place.

---

### Post by Pumalite on 2008-07-27
Here you have some other boot parameters you might want to try:
pci=noacpi irqpoll pnpbios=off all_generic_ide vga=0x317

---

### Post by bfuzze on 2008-07-27
Let me say first, thanks for the suggestions.  

Earlier I was making the mistake of removing the default boot options string when adding new boot options. A weird coincidence is that I created this boot disk from a workstation I named casper, so I thought those might have been left over configs from that station (I don't know why).

The default string is: 'file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --'

I tried appending the following to the default boot options string above (all except for 'quiet' so I could see where it stopped): 

'noapic acpi=off nolapic' - Plug n play instability error (see details below)

'noapic' - system freezes, as before, after io scheduler cfq

'nolapic' - system freezes, as before, after io scheduler cfq

'acpi=off' - Plug n play instability error (see details below)

'pnpbios=off' - system freezes, as before, after io scheduler cfq

'acpi=off pnpbios=off' - system freezes, as before, after io scheduler cfq
 
'pci=noacpi' - system freezes, as before, after io scheduler cfq 

'irqpoll' - system freezes, as before, after io scheduler cfq

'all_generic_ide' - system freezes, as before, after io scheduler cfq

'vga=0x317' - system freezes, no cursor at top of screen

'vga=771' - system freezes, no cursor at top of screen

Plug n Play Error: (paraphrased)
"Resource structure does not contain end flag"
update bios (I already updated the bios)
get_dev_node:unexpected status 0x37

The PnP error is at least different, so possibly a step in the right direction, but as show above when using 'pnpbios=off' or 'acpi=off pnpbios=off' it freezes at the same place.

I'll try changing the PnP settings in the bios to see if I get anything else.

Any other suggestions would appreciated, thanks.

---

### Post by Pumalite on 2008-07-27
Take a look at these:
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by bfuzze on 2008-07-27
Are there any kind error logging I can view during the load process, or step by step load option so I can determine if this error occurs with the io scheduler cfq or the step following...

I tried enabling PnP O/S and now the PnP error does appear, but the system freezes at the same spot.

---

### Post by Pumalite on 2008-07-27
It might be in /casper.log

---

### Post by bfuzze on 2008-07-27
how do I access casper.log

---

### Post by Pumalite on 2008-07-27
cat /casper.log

---

