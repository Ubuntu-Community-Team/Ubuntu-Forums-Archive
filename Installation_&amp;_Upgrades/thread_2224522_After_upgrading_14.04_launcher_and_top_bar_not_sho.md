---
title: "After upgrading 14.04 launcher and top bar not showing, short cuts not working"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by anton13 on 2014-05-16
Hi

I have upgraded two laptops (different brands) and have suffered the same problem.

I login, and can only see the background. Unity launch and top bar does not show.

I have tried the following:
```

sudo apt-get purge nvidia* bumblebee*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-nouveau
sudo apt-get install --reinstall ubuntu-desktop unity
sudo apt-get install compizconfig-settings-manager
sudo apt-get purge fglrx-*
mkdir ~/backup
sudo mv ~/.compiz ~/backup
sudo mv ~/.cache ~/backup

```

Have also tried advice from the folliowing:
[LIST]
[*][http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)
[*][http://askubuntu.com/questions/451159/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-14-04](http://askubuntu.com/questions/451159/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-14-04)
[*][http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login](http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login)
[/LIST]

Nothing has worked.

What have done, is create a new user, and this user has a working unity. However, as mentioned, I have not been able to fix my problem. 

Ive spent days on this issue, and nothing has worked. 
Any advice is greatly appreciated.

---

### Post by monkeybrain20122 on 2014-05-16
why are you uninstalling nvidia AND fglrx? What is your card? Why is bumble-bee in the mix? You said it is an upgrade, did you remove your proprietary driver (if any) first? the mesa drivers shouldn't need reinstall unless you have removed them yourself.

---

### Post by anton13 on 2014-05-16
> **monkeybrain20122 said:**
> why are you uninstalling nvidia AND fglrx? What is your card? Why is bumble-bee in the mix? You said it is an upgrade, did you remove your proprietary driver (if any) first? the mesa drivers shouldn't need reinstall unless you have removed them yourself.

I am simply trying what has been recommended in forum posts from others who have had the same problem.

I dont know what card I have. Intel I think. 

During the upgrade I didnt do anything but follow the ususal instructions. I dont know if proprietery drivers where removed.

---

### Post by su:bhatta on 2014-05-16
Please provide output of :

```
sudo lshw -short
```

Post output of the command within Code tags.

Please understand, Fglrx is proprietory drivers for AMD cards, bumblebee is for Nvidia, and nouveau is opensource drivers for Nvidia cards.
Proprietory drivers are not added by default. Did you install any separately in the initial install?

---

### Post by anton13 on 2014-05-16
Ok, here is the output:

```
Script started on Fri 16 May 2014 22:47:08 CEST
root@MagickLap001:/home/magick# sudo lightdm[5Plightdmsudo lightdm[Ksudo lshw -short 
  DMI      SMP      PA-RISC          device-tree              SPD      memory         /proc/cpuinfo                CPUID        PCI (sysfs)              ISA PnP          PCMCIA         PCMCIA         kernel device tree (sysfs)                             USB      IDE      SCSI       Network interfaces                     Framebuffer devices                      Display          CPUFreq          ABI       H/W path        Device     Class          Description 
===================================================== 
                           system         4174W8Y () 
/0                         bus            4174W8Y 
/0/1                       processor      Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz 
/0/1/2                     memory         64KiB L1 cache 
/0/1/3                     memory         256KiB L2 cache 
/0/1/4                     memory         3MiB L3 cache 
/0/5                       memory         4GiB System Memory 
/0/5/0                     memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns) 
/0/5/1                     memory         DIMM [empty] 
/0/e                       memory         128KiB BIOS 
/0/100                     bridge         2nd Generation Core Processor Family DRAM Controller 
/0/100/2                   display        2nd Generation Core Processor Family Integrated Graphics Controller 
/0/100/16                  communication  6 Series/C200 Series Chipset Family MEI Controller #1 
/0/100/16.3                communication  6 Series/C200 Series Chipset Family KT Controller 
/0/100/19       eth0       network        82579LM Gigabit Network Connection 
/0/100/1a                  bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 
/0/100/1b                  multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller 
/0/100/1c                  bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1 
/0/100/1c.1                bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 2 
/0/100/1c.1/0   wlan0      network        Centrino Advanced-N 6205 [Taylor Peak] 
/0/100/1c.3                bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 4 
/0/100/1c.3/0              generic        MMC/SD Host Controller 
/0/100/1c.4                bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 5 
/0/100/1c.4/0              bus            uPD720200 USB 3.0 Host Controller 
/0/100/1d                  bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 
/0/100/1f                  bridge         QM67 Express Chipset Family LPC Controller 
/0/100/1f.2                storage        6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller 
/0/100/1f.3                bus            6 Series/C200 Series Chipset Family SMBus Controller 
/0/0            scsi0      storage         
/0/0/0.0.0      /dev/sda   disk           128GB C300-MTFDBAK128M 
/0/0/0.0.0/1    /dev/sda1  volume         243MiB Linux filesystem partition 
/0/0/0.0.0/2    /dev/sda2  volume         119GiB Extended partition 
/0/0/0.0.0/2/5  /dev/sda5  volume         119GiB Linux filesystem partition 
/1                         power          42T4847 
/2                         power          51J0508 
root@MagickLap001:/home/magick# exit 
exit 

Script done on Fri 16 May 2014 22:47:28 CEST
```

---

### Post by su:bhatta on 2014-05-16
It seems you have got Intel Graphics card and generally that don't need any proprietory drivers.
Intel Graphics have open source drivers and are built into the Kernel itself.
You need not install either Fglrx or Bumblebee and Noveau doesn't apply for your hardware.

I don't have the right knowledge cause I don't use Intel Graphics card, so wait till someone else helps you there.

Couldn't help but notice you run the command as root through a script.
You need not have to do that, a simple opening of the terminal and typing 'sudo lshw -short' followed by your password would have sufficed.
It is not advisable to use root privileges, specially in Ubuntu installations.

---

### Post by elliotash on 2014-09-02
I am having a similar problem after upgrading to 14.05 all i see is a blank screen. I have tried many of the answers advanced and they have not worked so far. The last answer I was trying was a suggestion to install compizconfig-settings-manager. The problem I encountered while trying to do this was the message I got - Unable to fetch some archives. The message is long and I hope that I have no typos in typing the message - this is the message repeated a couple of times 
Error [http://ubuntu.mirror.constant.com/trusty-updates/universe](http://ubuntu.mirror.constant.com/trusty-updates/universe) python-compizconfig amd64 1:0.9.11.2*14.04.20140714-ubuntu1 could not resolve ubuntu.mirror.constant.com
Error [http://ubuntu.mirror.constant.com/trusty-updates/universe](http://ubuntu.mirror.constant.com/trusty-updates/universe) compizconfig-settings-manager all 1:0.9.11.2*14.04.20140714-ubuntu1 could not resolve ubuntu.mirror.constant.com
E: Failed to fetch [http://ubuntu.mirror.constant.com/pool/universe/c/compiz/python-compizconfig](http://ubuntu.mirror.constant.com/pool/universe/c/compiz/python-compizconfig) _0.9.11.2*14.04.20140714-ubuntu1 amd64.deb could not resolve ubuntu.mirror.constant.com
E: Failed to fetch [http://ubuntu.mirror.constant.com/pool/universe/c/compiz/python-compizconfig-settings-manager](http://ubuntu.mirror.constant.com/pool/universe/c/compiz/python-compizconfig-settings-manager) _0.9.11.2*14.04.20140714-ubuntu1_all.deb could not resolve ubuntu.mirror.constant.com
E: unable to fetch some archives, maybe run apt-get update or try with  --fixing missing?

The other problem is that I can only use the terminal on the machine using the CTRL-Alt-F1

Is there any way that  I can get the source list edited that I can modify, I am at my wits end

---

### Post by elliotash on 2014-09-02
Well there are new things happening now

If I log on as a non-admin user I get to the desktop, but the screen goes psychedelic after a minute and that's it the screen is a set of diagonal lines of different colours

---

