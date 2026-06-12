---
title: "Installation problems with HP dv6000"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by bunnii on 2006-09-21
I've been toying with different versions of Linux for a while, and finally got around to getting my mits on Ubuntu. I just got a new laptop and I want to try out Ubuntu on this, however, it doesn't appear to want to be tried out :(

I realise there may be a plethora of driver issues, especially because this is a shop bought laptop, but I feel the Ubuntu LiveCd should at least boot properly. 

At first, the installation didn't seemed to stall at VLM(sp?) section, but I left it for 15 minutes, and it stalled on the next step (I'm not seeing any errors, but it just seems to stall, the laptop is silent and the CD drive isn't active).

 Considering this might be a problem with the laptop I tried it on another machine (AMD Sempron 1.6ghz, 512 ram) and it fired through the bootup in a few minutes, and I could play around on the desktop.

So why is it failing to boot on my laptop?
I have noticed that the Cd/DVD drive isn't the fastest of cats around, so maybe I should just leave it for a while longer (pushing 20 minutes seems extreme .though)

The laptop is a HP Pavillion (Sempron 3400+, 512 ram)


regards,
bunnii

---

### Post by whizbaby on 2006-09-21
Download the *alternate install cd* and when it gives you a menu the first time you can select *expert mode*(I believe with 'F6'). You would have to look around on the net for what modules to load ...

---

### Post by |)arkFire on 2006-09-23
i successfully installed Ubuntu Dapper 64 from the alternate cd (only  after a few failed attempts with the live cd). it should be a simple process once you begin the install.

once you get it up and running you may have a few issue booting (make sure the wireless switch is turned off, and that in the grub command line you add either 'pci=noacpi' of 'acpi=off'). and not all the hardware will work (perhaps your sound, and deffinatly the wireless) good luck.

---

