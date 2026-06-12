---
title: "Installation and kernel panic"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by Dexy on 2012-12-06
Hello,

You are my last hope ... when i make a bootable USB drive i put it to a my computer i see a pink screen and then kernel panic ... i tryed the USB in my laptop and it works ... so i know it's not a USB...

Kernel error is:

```

[0.096011] 82480283 00315000 00d7b101 0049c00f 0083c00f c18ea18d 00000060 c17e45ec
[0.096011] c17e5682 00000004 f5079f68 00000001 000f0031 00000283 5f32335f 00000001
[0.096011] c18e9f9f 00000000 f5079f90 c18e9fc8 f5154800 c194f3b0 f5079fc0 c1003112
[0.096011] Call Trace:
[0.096011] [<c18ea18d>] ? pci_pcbios_init+0x186/0x255
[0.096011] [<c18e9f9f>] ? pcibios_resource_survey+0x2a/0x2a
[0.096011] [<c18e9fc8>] pci_arch_init+0x29/0x68
[0.096011] [<c1003112>] do_one_initcall+0x112/0x160
[0.096011] [<c18aeade>] kernel_init+0x11a/0x1b6
[0.096011] [<c18ae41c>] ? loglevel +0x2b/0x2b
[0.096011] [<c18ae9c4>] ? start_kernel+0x363/0x363
[0.096011] [<c15d04fe>] kernel_thread_helper+0x6/0x10
[0.096011] Code: 02 b6 07 80 e3 f8 0a de 66 bf 0a 00 e8 2c fd ff ff 72 18 66 81 f9 04 06 75 11 66 bf 1a 00 e8 f6 fc ff ff 72 06 38 d1 76 02 47 65 <6e> 75 69 6e 65 20 49 6e 74 65 6c 28 52 29 20 00 5f 66 5a 66 5b
[0.096011] EIP: [<c00f0446>] 0xc00f0446 SS:ESP 0068:f5079f38
[0.096011] CR2: 000000000000b101
[0.096011] ---[ end trace ca3e9e25dccc522f ]---
[0.104025] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000009
[0.104025]
```

I saw other topics about kernel so i runned memtest and 0 errors, and i was running windows fine, but i don't want windows anymore...


Hardware:

Motherboard: Conroe Kentsfield FSB1066
Power supply: Switching Power Supply ATX-400w
HardDrive: Seagate's Barracuda 7200.10 (250 GB)
Graphics card: ATi Radeon HD 56700 (1gb MSi Edition)
Processor: Intel Celeron E3500
RAM: G.Skill F2-6400CL5S-1GBNT DDRII1gb (x2)


If u need something else just ask, i realy want to run ubuntu :S
Thanks and sorry for my bad english, im from Croatia :)

---

### Post by 2F4U on 2012-12-06
I may have overlooked that information, but which version of Ubuntu are you trying?

---

### Post by Dexy on 2012-12-06
I tried 12.10 and 12.04, same result... i also tried a alternative versions and again same ...

---

### Post by Inoki on 2012-12-07
Maybe, just a guess, have you tried to update the BIOS on your computer? I've had a similar issue when I bought my laptop. I couldn't install anything, since my BIOS was outdated. (Funny how they ship lappies with older BIOS versions and not the newest ones.) Afterwards I was able to install anything normally.

---

### Post by Dexy on 2012-12-08
Ok, nice i updated bios and installed a ubuntu 12.10 but when it goes to desktop i don't see anything except background ...

---

