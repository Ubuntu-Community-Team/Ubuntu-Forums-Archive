---
title: "Installation problem, stops at kernel_thread_helper+0x6/0x10"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by tkboing on 2012-01-20
I tried to install Ubuntu 11.10.
I made liveUSB. I checked it, the iso file is ok.
But I can't install it.

I also tried to Ubuntu 10.10 - the same effect
I tried to install using Wubi - the same effect.

I find this error after the ubuntu purple screen
[IMG]http://img815.imageshack.us/img815/1473/dsc00032j.jpg[/IMG]

Can you specify the problem and give a solution?


My computer:
Processor: AMD Athlon II x2 255 s.AM3
Motherboard: MSI 870-G54 s.AM3
RAM: GoodRam 2x2GB DDR3-1333 Dual Chanel CL9
HDD: WD Caviar Blue WD5000AAKX 500GB sATA III 16MB
Power supply: Enermax NANX ENP450AGT 450W
Graphics: Gainward GTS450 1024MB 128bit PCI-E DDR5

Thank You in advance for help.

---

### Post by bcbc on 2012-01-20
Use 'nomodeset' to boot: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Then check for 'additional-drivers' for your graphics card.

---

### Post by tkboing on 2012-01-21
I tried nomodeset as you suggested but still I got the **kernel_thread_helper+0x6/0x10**

The text mentioned that maybe I should try using noacpi, nolacpi and acpi=off. I tried all of the above and nothing helped.

Then I wanted to try again with nomodeset and an error message came out: **/casper/initrd.lz read error**

What is wrong?

My monitor is: LG 18.5 E1960S-PN LED

---

### Post by bcbc on 2012-01-21
There could be a couple of issues here. You need the nomodeset for that graphics card.

But the read error seems more likely to be a problem with your USB.

---

