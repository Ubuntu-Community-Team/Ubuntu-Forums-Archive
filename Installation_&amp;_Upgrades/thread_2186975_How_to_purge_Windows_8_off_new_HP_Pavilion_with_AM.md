---
title: "How to purge Windows 8 off new HP Pavilion with AMD Quad-core A8-5500"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by megenk11 on 2013-11-10
How to purge Windows 8 off new HP Pavilion with AMD Quad-core A8-5500. I hear about issues removing drivers etc.. My roommate gave up and returned box as it's Ubuntu or bust. I do not give up and I have you to thank, as I have great team assisting this OS toddler. 
I am shelving my 1Gb dell gx-240 and in 36 hours arrives the new box.
I am very concerned that Windows 8 will be installed and need to know; how to remove all Microsoft;  when and how to install the first 64 bit (Ultimate Edition); May I swap in the HDD 250Gb 32 bit running Zorin 6 that I am using now and start there? Can a 64 bit run 32 bit software?
The new box being delivered in 25 hours is a:
HP Pavilion Desktop - 8GB Memory - 1TB Hard Drive - 64 bit
AMD Quad-Core A8-5500 Accelerated Processor with AMD Radeon HD 7560D graphics, and _4MB L2 cache memory_ (Bios only? Could it grub2 also?) I have only been able to boot 1 OS per HDD, and I'll stack 7200 rpm HDDs until I learn to boot from an inner partition. What is uefi and is USB or DVD the best Ubuntu install?
Terminal cancer (hah!) aside, this is so important to me, to get Win-8 Out and finally be able to really use these beautifully crafted programs, 1 Gb was tough. I am hoping to build a working audio studio and even saved $ for interface box, but first I must get support in loosening Microsoft's hold over my biggest system Yet. 
Please send any info! I am a terminal user, n-curses if I must, and actual code helps best.
I am truly glad that you fellow Open sourcers are out there!
Thank you, Meg

---

### Post by oldfred on 2013-11-10
If not familar with UEFI, it is a big change. Instead of one boot mode BIOS, you now have three, UEFI with secure boot, UEFI, and BIOS/CSM/Legacy or whatevery your UEFI calls the old way.

I would not intially remove Windows. Some have modified UEFI to only boot Windows. There is a work around but it requires renaming the Windows boot files to really be grub2's shim that has the Microsoft signing key. System still thinks it is booting Windows but really is booting grub.

New UEFI systems also use gpt partitioning instead of the 35 year old BIOS partitioning. Windows only boots from gpt with UEFI, Ubuntu can boot in either UEFI or BIOS boot mode from gpt, but all systems can only boot from MBR(msdos) partitioning in BIOS mode. I suggest saying with gpt as it is newer & better.

You only want 64 bit Ubuntu or one of the other flavors if you do not like Unity. I run Ubuntu but with fallback/flashback. 
Some of the very new Haswell processors really need the very newest version of Ubuntu or 13.10 as kernel & Intel drivers have many new updates for the new processors.

Please review link in my signature for more (maybe too much) info.

---

