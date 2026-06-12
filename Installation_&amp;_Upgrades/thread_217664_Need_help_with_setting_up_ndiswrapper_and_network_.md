---
title: "Need help with setting up ndiswrapper and network card"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by secondvijai007 on 2006-07-17
Hi! 
[INDENT][/INDENT]I'm writing this with hopes that someone here can help me fix a problem regarding my wireless card. I just recently upgraded to Dapper Drake from Breezy (I upgraded, didn't do a fresh install). Everything seems to work fine now (after some tweaking) except my network card. 

[INDENT][/INDENT]For some reason, my wireless settings disappeared during the upgrade (probably because of the newer version of ndiswrapper on dapper) and ubuntu has renamed my wlan0 interface as eth1. I don't think that this is a problem, as long as everything else is configured correctly. My wireless card is a Motorola WN825G, which worked perfectly well on my copy of breezy with the driver bcmwl5. So I went through the ndiswrapper wiki and followed all the instructions, and everything seemed to go smoothly until I saw that my network card refused to power on after the modprobe ndiswrapper command.

[INDENT][/INDENT] I've tried to do as much research as possible and find a solution on my own, but i'm not able to find anything that can help me fix this problem. Here is what I know:
> 
ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl5a         driver present, hardware present
(I added bcmwl5a just for good measure...)

> dmesg
[7179606.048000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
^ It does NOT, (like it's supposed to according to the wiki) say that bcmwl5 is added in dmesg.<-- this is the only thing relevant to ndiswrapper (i didn't want to confuse or waste space by pasting the whole thing) 

when i type iwconfig
> 
eth1      IEEE 802.11b/g  ESSID:"2WIRE628"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr-off   Fragment thr-off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



I see that the word wlan0 is mentioned in several system files, so i went back and changed it to eth1, but i wasn't sure about what that would do so i changed them back. I don't think this is why my card isn't even powering on...

Like I said, the only thing off seems to be that in dmesg, the names of the drivers are missing. I'm guessing that's why the power is not coming on, because the drivers don't show up as being added -- or I could be wrong. It's supposed to say that the driver is loaded according to the wiki

Please help! I'm out of ideas and plus, I'm not an expert at this but I'm open to trying anything. According to dmesg, the laptop does recognize that there is something inserted into slot 1.

Thanks

---

### Post by secondvijai007 on 2006-07-17
Here is what i'm seeing in the system log

Jul 17 16:16:39 localhost kernel: [17182590.088000] pccard: CardBus card inserted into slot 0
Jul 17 16:16:39 localhost kernel: [17182590.088000] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
Jul 17 16:16:39 localhost kernel: [17182590.088000] ACPI: PCI Interrupt 0000:09:00.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

What does PCI interrupt mean and could it possibly have something to do with why my card doesn't turn on?

---

### Post by secondvijai007 on 2006-07-21
Well, it has been quite a while since my last post, but I've finally found a solution to this problem. I'm posting this just so that anyone else in my predicament can go back and fix this annoying problem. The reason why my card refused to turn on because there was another ndiswrapper-like module that came with dapper, called bcm43xx. This was trying to attach onto my pcmcia card, which refused to communicate with this module. In order to remove this module and use ndiswrapper, here's what you do:

first "blacklist" the bcm43xx module: 

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx

Install ndiswrapper 
^> If you had already done so, and you were able to see successfully, 'hardware present'
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

The light should come on.

---

