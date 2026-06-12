---
title: "highpoint 7502 Raid Controller"
date: 2022-12-21
forum: Installation &amp; Upgrades
---

### Post by scmeis1 on 2022-12-21
Hi,
   my first ever post here. I have never beeen so stumped. I have a new raid controller 7502, just needed something basic for my Ubuntu 22.04 install. However, no matter what I do, the Raid 1 is not recognized. highpoint's directions always involve after the install which blew up my current install. What is the process to install the highpoint binary to get Ubuntu 22.04 to recognize this Card.

BTW: I do have secure boot disabled on the mother board.

Motherboard is: Asrock Z690 phantom gaming 4/d5

---

### Post by SeijiSensei on 2022-12-21
Which card and driver?

[https://www.highpoint-tech.com/linux/ubuntu](https://www.highpoint-tech.com/linux/ubuntu)

I downloaded one of these which came as a tar.gz. I unzipped that and found a .bin. I would run the binary by first making it executable with 
```
$ chmod a+x hptnvme_g5_linux_src_v1.4.1_2022_03_04.bin 
```
or the equivalent file for your card. Then you should have run the binary with
```
$ sudo ./hptnvme_g5_linux_src_v1.4.1_2022_03_04.bin
```

Is that what you did? What happened?

You might then have needed to tell the kernel to use the driver with modprobe. See "man modprobe" for details.

---

### Post by scmeis1 on 2022-12-21
I know that, how about install. I did the install of that binary on my active server and it blew up. All the UID's are now invalid and i am unable to see any drives. So i have no choice but to reinstall. The question is how to get that binary or driver to install so that on the install it sees the hardware Raid 1.

---

### Post by scmeis1 on 2023-03-03
I had hoped to get a response by now so i will try again.

Ubuntu 22.04 server installation. BRAND NEW INSTALLATION

ASrock Z690 phantom 4/D5 bios see's highpoint 7502 and Raid 1 that is configured.

upon running the ubuntu installation I have chosen both the normal Kernel and HWE kernel for install. I get to format of drives, and I see both NVEm.2 drives on the Highpoint but No Raid 1 logical drive. I do not want to install on a single physical drive, i want to use the Raid 1 i configured.

I have been searching for weeks for a way for me to install Ubuntu 22.04 on the Raid 1 i created but Ubuntu never sees it. I am extremely frustrated. I know about the open source drivers but I have no idea how to have them installed into the installation USB drive.

---

### Post by MAFoElffen on 2023-03-03
More info needed.

Please run the [Ubuntu 'system-info' script]("https://github.com/UbuntuForums/system-info") from a LiveCD, so we can see how how Linux sees the RAID Card as a storage controller. Please post the URL of where the report uploads the report to.

You can do this from the Ubuntu Server Live Installer by starting an install, going to the "help" link > 'System Prompt', to get you to a command line. Then:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info

```
And snap a picture of how your BIOS see's the Highpoint card and the RAID1 member of it... You said your system's BIOS see's all that without any drivers loaded, so there must be some type of on-card BIOS(?)

---

