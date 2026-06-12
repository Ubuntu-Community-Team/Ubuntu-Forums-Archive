---
title: "trying to boot from live cd"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by igoclimbingnaked on 2007-07-28
alright when i try to boot from the cd it crashes in the loading hardware drivers section

I know the cd and the disk drive do work

Its a dell inspiron 2350 with some not stock items
The mother board is a Mitac with a Intel 845 (brookdale) Chipset
My processor is an intel pentium 4 with 2.0 ghz
My graphics card is an Nvidea GeForce4 MX 4000
I have roughly 750mb of ram
My hardrive is a WDC WD400BB-75FJA1 40gb ata....im thinking it has something to do with this.

any ideas anyone

---

### Post by Pumalite on 2007-07-28
Try Alternate CD.

---

### Post by igoclimbingnaked on 2007-07-28
ive installed it from an alternate cd before and it kept crashing....so im doing it from the live so i can figure out whats wrong before i install it again.

---

### Post by Pumalite on 2007-07-28
Go to BIOS and make sure there is Advanced Support for PATA+SATA.

---

### Post by igoclimbingnaked on 2007-07-28
sry but can you tell me how to do that exactly....sorry if it seems obvious im a little slow

---

### Post by Pumalite on 2007-07-28
In BIOS there should be a section for 'IDE Configuration'. Look there.

---

### Post by igoclimbingnaked on 2007-07-28
k will do in a sec and by the way the last line of text it shows when it crashes is

EIP: nativ_apic_write_atomic+0x6/0x10 SS:ESP 0068:e49fbe8c

---

### Post by Pumalite on 2007-07-28
You might wany to look at these too:

[http://www.linux.it/~napo/index.php/Main/LinuxOnMitac8060](http://www.linux.it/~napo/index.php/Main/LinuxOnMitac8060)

[https://answers.launchpad.net/ubuntu/+source/yelp/+question/7518](https://answers.launchpad.net/ubuntu/+source/yelp/+question/7518)

---

### Post by igoclimbingnaked on 2007-07-28
alright as far as advanced sata support etc theres no option for that....but the harddrives not new its working perfect on windows...basically im looking for a (boot:) type command to make this work cuz i think thats all i need. ive tryed noapic and a few others

---

### Post by igoclimbingnaked on 2007-07-28
sorry for the smiley its supposed to be a  (boot:  ) type command

---

### Post by igoclimbingnaked on 2007-07-28
ohh and sorry its a dimension not a inspiron

---

### Post by Pumalite on 2007-07-28
Install with Alternate CD and at the command line after reboot:

sudo dpkg-reconfigure xserver-xorg

Choose most defaults, but 'vesa' as the driver.

---

### Post by igoclimbingnaked on 2007-07-28
how would i get to the commandline when ubuntu never loads when i install it...

---

### Post by Pumalite on 2007-07-28
I'm out of ideas. Someone that knows better will jump in. Patience.

---

### Post by igoclimbingnaked on 2007-07-28
alright thx tho

---

### Post by igoclimbingnaked on 2007-07-29
bump

---

### Post by igoclimbingnaked on 2007-07-29
bump any help please

---

### Post by igoclimbingnaked on 2007-07-29
bump

---

### Post by Pumalite on 2007-07-29
You are better off starting a new thread with something like 'Mitac 845 chipset install' or something. Maybe in Hardware.

---

