---
title: "Installation problems Ubuntu Server on Alix 1D w/ 8GB CF card"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by lennynpeter on 2016-02-26
[h=2]Please HELP! :confused:[/h]I’m looking for a solution for the following problem. I was running Ubuntu Server 10 for several years on a PCEngines Alix 1D system board without problems, but unfortunately forgot the password and do not remember which procedure I used the first time to install Ubuntu Server on an 8GB CF card so I decided to re-install and upgrade at the same time. Since the Alix 1D refuses to boot from a USB drive (have tried different model, different sizes) and after following several other procedures on the web without success I did as listed below. The same procedure works well for another Alix board 2D3 without a hassle. Beside the final version of Ubuntu Server (15.10) I tried to install from 12.04 up every version in different ways – no luck!
 
[h=2]Hardware:[/h]PCEngines Alix 1D system board
Phoenix AwardBios v6.00PG
AMD-LX800-6A43AEM1C-00  1/16/2009
8GB Compact Flash card as main hard drive
 
[h=2]OS:[/h]Ubuntu Server 15.10 LTS x32
 
[h=2]Installation Sequence:[/h]
[LIST]
[*]Ubuntu Server 15.10 LTS x32.iso installed to a 2GB USB thumb drive
[*]‘stripped’ laptop (no hardrive, no CD/DVDROM, no SD/CF cards) booted with prepared USB thumb drive
[*]Installation progresses flawless (detects the laptops network card, but does not generate the file /etc/udev/rules.d/70-persistent-net.rules)
[*]Create partitions:
[LIST]
[*]/dev/sdb1           255MB Ext2 Linux (Bootable)
[*]/dev/sdb2           7.8GB Extended
[*]/dev/sdb5           7.8GB LUKS
[/LIST]

[*]During GRUB installation /dev/sdb1 was listed as /dev/sdb to install GRUB
[/LIST]
 
[h=2]Startup after installation completion:[/h]
[LIST]
[*]Using the ‘stripped’ laptop system starts up without any problem and works as expected
[*]Using the CF card in the Alix 1D board the following happens:
[LIST]
[*]After reset displayed message – Award Preboot Installation Agent Failed
[*]Grub screen appears (GNU GRUB version 2.02~beta2-29) with option:
[LIST]
[*]Ubuntu
[*]Advanced options for Ubuntu
[*]Memory test (memtest86x)
[*]Memory test (memtest86x, serial console 115200)
[/LIST]

[*]Whatever choice is made – black screen and restart
[/LIST]
[/LIST]
 
Honestly I really need the Alix 1D to work, but I’m running out of options and would appreciate any help very much. Thanks in advance for even the tiniest hint that could help to resolve.:D
 
Cheers,

Peter

---

