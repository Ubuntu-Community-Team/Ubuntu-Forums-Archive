---
title: "HP DV6338SE Install Woes..."
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by sw40c on 2007-04-12
I'm a somewhat experienced Ubuntu user (Fiesty herd 2 on my self built desktop, total Ubuntu time about 1 year) but I'm having a devil of a time installing Ubuntu Edgy/Fiesty 64 bit on my HP dv6338se laptop.  Config is: 

Product Name  dv6338se  
US Product Number  RV009UA#ABA 
Microprocessor  1.8 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-56 
Microprocessor Cache  512KB+512KB L2 Cache 
Memory  1024MB DDR2 System Memory (2 Dimm) 
Video Graphics  NVIDIA GeForce Go 6150 (UMA) 
Hard Drive  160GB 5400RPM (SATA) 
Multimedia Drive  LightScribe Super Multi 8X DVD±R/RW with Double Layer Support 
Display  15.4" WXGA High-Definition Brightview Widescreen (1280 X 800) 
Fax/Modem  High speed 56k modem 
Network Card  Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector) 
Wireless Connectivity  802.11b/g WLAN  
other info deleted - i.e. sound ports, vga out, etc.


I got the laptop the other week at BestBuy beacuse HP is pretty well known to be at least somewhat linux friendly...  Well, I knew I wanted to stick to the 64 bit versions of Ubuntu to take advantage of my architecture.  After no sucess with default boot settings I tried the boot solutions put forward in the dv6000 installation wiki (see [here]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)")).  Still no dice - it freezes when booting into the GUI.  It would appear I need a separate driver for my graphics card but I can't find any mention of the GeForce 6150 driver appearing as an option on either the Edgy or Fiesty install disks.

I then tried the alternate install CDs of both Edgy and Fiesty and it would not let me partition my HD!  It is SATA and not a RAID so no special options should be mentioned at boot time, correct?

Please help, I'm totally lost here!
Matt :(

---

### Post by yevelez on 2007-04-21
hello. I have exactly the same laptop. I came here looking for some help, but I think is my responsibility to help you as so many times I have been helped. i think that the problem with your CD might be the bug that ubuntu has with the apic and lapic...dont ask me what that means, but is has it...

So the only thing you have to do is to boot your computer, and at the time to select if you want to start or install ubuntu, and the other options, you should press F6 and copy these two words:
noapic nolapic
after that press enter and your laptop will run wonderful ubuntu!!!

I hope this can help you

---

### Post by jdong on 2007-04-21
> **sw40c said:**
> 
I got the laptop the other week at BestBuy beacuse HP is pretty well known to be at least somewhat linux friendly... 

Say what? Not all of them; just a few line of HP's have been certified with Linux; it's definitely not a good assumption to make that HP == Linux-friendly. Just a reminder for anyone else watching this thread.

> 
 Well, I knew I wanted to stick to the 64 bit versions of Ubuntu to take advantage of my architecture.  
That's not generally true. In most cases you will not see a performance difference between 32-bit and 64-bit Ubuntu, unless you do some very specific kinds of work optimized for 64-bit already. In general, stick with 32-bit distributions because they tend to be more tested against bugs.

> 
 It would appear I need a separate driver for my graphics card but I can't find any mention of the GeForce 6150 driver appearing as an option on either the Edgy or Fiesty install disks.

The nvidia drivers are available to download after you install... if the GUI freezes while booting, try the failsafe GUI mode, and if that fails, the alternate CD.

> 
I then tried the alternate install CDs of both Edgy and Fiesty and it would not let me partition my HD!  It is SATA and not a RAID so no special options should be mentioned at boot time, correct?

What error(s) do you get?

---

