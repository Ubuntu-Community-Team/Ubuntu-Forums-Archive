---
title: "Input output error when try to install ubuntu"
date: 2018-02-01
forum: Installation &amp; Upgrades
---

### Post by tomert on 2018-02-01
Hi.

I had 16.04 LTS on my Asus R558UQ. Everything worked fine almost a year, but 3 weeks ago my Ubuntu crashed. I had to reinstall OS, and then I had a lot of trouble with drivers for my Nvidia GPU. I tried different distros (Ubuntu 16.04, 17.10, Manjaro, Mint) and system always crashed after some days. I blamed Nvidia but soon after that I started to have an issue during installation.

Now I can't install ubuntu because of "fsyncing/closing/dev/sda: Input/output error" Again, I tried different distros, tried GParted, PMagic, completely erase HDD ,whit /dev/zero; hdparm. Nothing works for me.

My HDD: Seagate 1TB HDD 7MM, ST1000LM035

I have seen some similar topics but haven't found any solution to fix it.

---

### Post by tinylagarto on 2018-02-01
How did you try to install Ubuntu? From a bootable USB or CD?

---

### Post by Impavidus on 2018-02-02
I/O error when writing to a freshly formatted hard drive, that sounds like a broken hard drive. Maybe you wish to run a few checks.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by tomert on 2018-02-02
Thank your for your answers.

> **ivanovnegro2 said:**
> How did you try to install Ubuntu? From a bootable USB or CD?

Yes. I used bootable CD

@Impavidus
I will run these checks later and will let you know.

---

### Post by tomert on 2018-02-03
I used bootable CD with Ubuntu 17.10 to make test

When I type:
*sudo smartctl -i /dev/sda *

I got:
 [I]Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.[/I]

And then the same problem:
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
fdisk: cannot open /dev/sda: Input/output error


I tried to make the same test on Slax but then I got:
 [I]Read SMART Data failed: scsi error badly formed sci parametersfdisk
[/I]

I also noticed that HDD disappears sometimes in BIOS.

---

### Post by tomert on 2018-02-05
OK. I'm going to buy a new hard drive.

Thread solved

---

