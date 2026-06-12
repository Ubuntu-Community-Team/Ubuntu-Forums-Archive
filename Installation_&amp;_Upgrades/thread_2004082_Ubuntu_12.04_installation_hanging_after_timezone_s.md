---
title: "Ubuntu 12.04 installation hanging after timezone selection"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by deepakmenon on 2012-06-15
I am trying to instal Ubuntu 12.04 LTS 64 bit on my HP Dv6 6121Tx laptop. The laptop have the below configuration and comes with with a preloaded Windows 7 Home premium.
i7 2630qm 
8GB RAM
AMD 6770M 2GB GDDR5 
640 GB 5400 rpm

I am trying to install Ubuntu to an external Western Digital solid state HDD with USB 3.0 support. After downloading the ISO file, I created a bootable USB stick with the help of pen drive linux. I was able to boot up the laptop from the USB stick and begin installation. The Portable harddisk was detected and I was able to partition the  disk and start installation. However, after the timezone selection screen it kind of hung up. The "Continue" button was greyed out and system was frozen. Waited for almost an hour and finally gave up. Retried couple of time without any success.

Can someone throw some light on possible causes? I am able to run Ubuntu from the USB stick without issues and start the installaer. But every time the installer will give up in the time zone selection screen :(

---

### Post by foxy123 on 2012-06-15
> **deepakmenon said:**
> I am trying to instal Ubuntu 12.04 LTS 64 bit on my HP Dv6 6121Tx laptop. The laptop have the below configuration and comes with with a preloaded Windows 7 Home premium.
i7 2630qm 
8GB RAM
AMD 6770M 2GB GDDR5 
640 GB 5400 rpm

I am trying to install Ubuntu to an external Western Digital solid state HDD with USB 3.0 support. After downloading the ISO file, I created a bootable USB stick with the help of pen drive linux. I was able to boot up the laptop from the USB stick and begin installation. The Portable harddisk was detected and I was able to partition the  disk and start installation. However, after the timezone selection screen it kind of hung up. The "Continue" button was greyed out and system was frozen. Waited for almost an hour and finally gave up. Retried couple of time without any success.

Can someone throw some light on possible causes? I am able to run Ubuntu from the USB stick without issues and start the installaer. But every time the installer will give up in the time zone selection screen :(

I had a similar problem with 12.04 on my Asus laptop and the issue was with the partitioner. Try to do all partitioning manually or the alternative ISO.

---

### Post by deepakmenon on 2012-06-15
Thanks Foxy. I was using manual partitioning only. I will anyway try with alternate iso.
Is there a way to find out what exactly is causing the installer to hang?

---

### Post by deepakmenon on 2012-06-22
Downloaded the alternate iso (64bit) and tried to install using the same method.
Created a bootable USB stick and installing to portable hard disk. Selected manual partitoning and installation was smooth. GRUB was installed to portable hard disk.

After installation when the system rebooted, I got only a blank screen. No grub, nothing.

Windows is booting up properly when the portable harddisk is removed. However, if the portable disk is connected I am getting only a blank screen. Can someone help.

---

