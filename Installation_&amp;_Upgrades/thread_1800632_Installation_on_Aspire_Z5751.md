---
title: "Installation on Aspire Z5751"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Einfachlacm on 2011-07-09
Hi,

I post my question here because i don't know why i can't install any OS in my new computer.

It's the Acer Aspire Z5751 ([http://support.acer.com/mx/es/acerpanam/desktop/2010/acer/aspire/AspireZ5751/AspireZ5751nv.shtml](http://support.acer.com/mx/es/acerpanam/desktop/2010/acer/aspire/AspireZ5751/AspireZ5751nv.shtml)). The AIO's characteristics are:
- Intel i5 3,2 Ghz
- Nvidia GT320M  1024 Mb
- 6 Gb ram ddr 3
- Hd 1 tb
- Monitor 23'

I tried already with those USB live and CD live:
- Ubuntu 11.04 64 bits
- Mint 11 64 bits
- Mint 10 KDE 32 bits
- Mandriva 2011 RC 1 64 bits
- ElementaryOS 0.1

With all of them the result was the same, after the BIOS booting i have a black screen and nothing happens.

But what is bizare ist that with all old versions before Ubuntu 10.04 (i tried 10.04, Mint 7, Mint 7 KDE, 9.04, Mint 7 XFCE) with a CD live (not with a USB live) it works. But my problem is that internet doesnt work (WIFI isn't detected and neither Ethernet cable -weird!!!-)

I find this link, but i don' understand very well: 
BIOS for Linux Updates default SATA mode to 'Native IDE'. 
[http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3351](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3351)

Maybe i should flash the BIOS, but how can i do tat in linux? I've seen the tutorial just in Windows and MSDOS.

Now i have 10.04 without internet

Do you have any idea what can i do?

Thanks!

---

### Post by Einfachlacm on 2011-07-12
Linux Mint Debian Edition loads the grub and then in "normal mode" and "compatibily mode" i get this error: "device descriptor read/64 error -110".

Linux Mint 11 in normal and compatibility modes executes the OS in the terminal (without grpical mode), and i get this error:  "shell-init: error retrieving current directory: getcwd: cannot acces parent directories: No such file or directory." I type "startx" and i get this: "getcwd failed".

I've installed the new BIOS:
BIOS for Linux Updates default SATA mode to 'Native IDE'. 
[http://support.acer.com/us/en/product/d](http://support.acer.com/us/en/product/d) … delId=3351

I've tried everything with both modes:  "Native IDE" and "AHCI". This options are in "Integrated Peripherals > Onboard SATA mode". The results are the same.

Windows 7 and Ubuntu 10.04 (without WIFI and Ethernet) work.

Do you know what can i do?

Thanks.

---

### Post by Einfachlacm on 2011-07-17
Finally I installed Mint 11 with a live CD and "noapic" and it worked.

---

