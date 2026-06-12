---
title: "Installing lubuntu on a 2gb cf card, AMD Geode LX800 AMD Geode LX800"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by Bahador_Boroumand on 2014-06-14
hi everybody,

i have an alix.3d3 with the following specs currently running win xp sp3 32bit. i use it for sharing wifi over lan with connectify, but the cpu goes to 100% sometimes and it makes some problems for connectify service. alternatively i want to install lubuntu to do the same task with putting the ethernet on sharing mode, but i cant install lubuntu cuz it says at least 4.4GB free space is required. what should i do?

&#8226; CPU: 500 MHz AMD Geode LX800 
&#8226; DRAM: 256 MB DDR DRAM 
&#8226; Storage: 2GB CompactFlash
&#8226; Power: DC jack or passive POE, min. 7V to max. 20V 
&#8226; Connectivity: 1 Ethernet channel (Via VT6105M 10/100) 
&#8226; Firmware: Award BIOS

tnx...

---

### Post by ajgreeny on 2014-06-14
Try something much smaller.

[Puppy]("http://www.puppylinux.com/") is probably worth a try, but even that may be pretty slow on such a machine.

---

### Post by yancek on 2014-06-14
You could try the Ubuntu usb-creator or unetbootin to put it on the card as a Live system with persistence.  Using either will give you an option to create a persistence file so you can save changes and the system will be the same size as the download which is just under 1GB.

---

### Post by kalehrl on 2014-06-15
It is possible using netinstall, or alternate install and choosing minimal system.
This will give you command line system without any GUI.
After that, you can install lubuntu-core or, for a really minimal lubuntu system, lubuntu-core --no-install-recommends.
My lubuntu is just 1.7GB big.
I also have Debian wheezy LXDE installed on a 1GB CF card.
The whole system is just over 600MB with the programs I use.
[COLOR=#ff0000]EDIT[/COLOR]: Are you sure your CPU is still supported?
I think I read somewhere that AMD Geode processors were dropped from the kernel a couple of cycles ago.

---

### Post by sudodus on 2014-06-15
> **ajgreeny said:**
> Try something much smaller.

[Puppy]("http://www.puppylinux.com/") is probably worth a try, but even that may be pretty slow on such a machine.

+1

***Wary Puppy, Tiny Core ***or*** DSL*** might work in that old computer.

---

### Post by mörgæs on 2014-06-15
> **kalehrl said:**
> Are you sure your CPU is still supported?
I think I read somewhere that AMD Geode processors were dropped from the kernel a couple of cycles ago.

Yes, please try if 14.04 runs in a live boot.

---

### Post by Bahador_Boroumand on 2014-06-15
i haven't tried it in my sbc yet... i just wanted to check the performance in vm... i'm gonna try to boot it live mode and post the results here... i hope the cpu is yet supported... :/ if successful, i'll try what kalehrl said...

---

