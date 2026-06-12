---
title: "Dual boot Gutsy - separate or single drives"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by NJC on 2007-10-22
I want to install Gutsy to an old Dell but need wisdom on the dual boot config:

Plan A/ Install Gutsy - separate partition - on a Win98 37gb drive; 30gb free

Plan B/ Install Gutsy on separate drive; install 37gb as second hard drive

Plan A will wipe out Win's MBR, I'll assume. Plan B will work, although I don't know if a Win drive will boot from Slave position. My current dual boot config consists of 2 drives:

hda   Win 37gb Master
hdb   Linux 6.06 Slave 

I always boot from hdb and have Win as a Grub entry. *BUT*, my crappy Dell won't allow booting from Slave. **Question**: Would Win boot from Grub using the following config:

hda   Linux 7.10 Master
hdb   Win 37gb Slave

Thoughts/wisdom/any 2 bit opinion welcome :wink: In the meantime, I'm off to hermanzone for more info: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Pumalite on 2007-10-22
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by NJC on 2007-10-22
pumalite, thanks for the links. Both links are for "Plan A", installing both OS'es on single drive. To be honest, that makes me nervous since I've always kept both OS'es on separate drives. But I do have a backup Win drive though in case it implodes. 

Re my question of booting Windows from a 2nd or 3rd disk location, that info [can be found here.]("http://www.users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands")

---

