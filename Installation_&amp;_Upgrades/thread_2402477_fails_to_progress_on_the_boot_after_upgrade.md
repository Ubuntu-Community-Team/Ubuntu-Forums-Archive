---
title: "fails to progress on the boot after upgrade"
date: 2018-09-30
forum: Installation &amp; Upgrades
---

### Post by fabio61 on 2018-09-30
Today I decided to upgrade form ubuntu 17.10 (that I used with Xfce) to 18.04.1 LTS.
After the upgrade I am not able to get into the system: I get the initial splashscreen (the screen with the "ubuntu" sign with the dots underneath that show the progress of the booting) but after a few moments (with the dots showing progress) the mouse pointer appears on the screen and everything stops.

I tried several options and I was able to get into the system starting a recovery session, activating the network from there, and then pressing contol-c to obtain the password prompt. At this point everything seems working but the resolution is very poor (everything is fuzzy) even if the "screen" settings shows a 1280/1024 resolution (but it is obvious that the dimensions on the monitor are ok but the graphic aspect is not)

Obviously, if I try to boot the system again I get to the same frozen screen after a few second of splashscreen. I can only get in with the recovery/network activation/control-c routine.

This is my hardware:

```
lshw -short
WARNING: you should run this program as super-user.
H/W path     Device      Class       Description
================================================
                         system      Computer
/0                       bus         Motherboard
/0/0                     memory      1983MiB System memory
/0/1                     processor   Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.8
/0/100                   bridge      82G33/G31/P35/P31 Express DRAM Controller
/0/100/2                 display     82G33/G31 Express Integrated Graphics Contr
/0/100/1b                multimedia  NM10/ICH7 Family High Definition Audio Cont
/0/100/1c                bridge      NM10/ICH7 Family PCI Express Port 1
/0/100/1c/0  enp1s0      network     RTL8101/2/6E PCI Express Fast/Gigabit Ether
/0/100/1d                bus         NM10/ICH7 Family USB UHCI Controller #1
/0/100/1d.1              bus         NM10/ICH7 Family USB UHCI Controller #2
/0/100/1d.2              bus         NM10/ICH7 Family USB UHCI Controller #3
/0/100/1d.3              bus         NM10/ICH7 Family USB UHCI Controller #4
/0/100/1d.7              bus         NM10/ICH7 Family USB2 EHCI Controller
/0/100/1e                bridge      82801 PCI Bridge
/0/100/1f                bridge      82801GB/GR (ICH7 Family) LPC Interface Brid
/0/100/1f.2              storage     NM10/ICH7 Family SATA Controller [IDE mode]
/0/100/1f.3              bus         NM10/ICH7 Family SMBus Controller
/0/2         scsi0       storage     
/0/2/0.1.0   /dev/cdrom  disk        DVD-RAM GH10L
/1           scsi2       storage     
/2           scsi3       storage     
/3           scsi4       storage     

```


```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
```

---

### Post by fabio61 on 2018-10-01
Any clues?

---

### Post by jessieinnewy51 on 2018-10-03
I have had a similar problem and it was resolved with the Information provided BELOW.
[LEFT] In my case I had the Problem with UBUNTU Version 18.04 after an upgrade from Version 17.10 and then I tried a complete New Installation of 18.04 which would not boot through to the Login Screen.

 In my Case it happened on a Desktop With the Graphics Card INTEL G33 in conjunction with Intel Dual Core, CPU E 5400,2.7Ghz,Motherboard Elite Group G31T-M

 

Easiest fix for me:

[LEFT]When you get to the Main Selection Menu on the screen follow the instructions below, (It appears that their is a Problem With Intel Graphics cards in conjunction with Gnome3, refer to previous Forum Discussion for Advanced information)
[/LEFT]
In Grub, choose "Advanced options for Ubuntu", then boot the latest "Recovery Mode" kernel. (4.15.0.29)
At the Recovery Mode menu, choose Resume. Ubuntu should boot more or less normally.
Log in.
Open a terminal window with Ctrl-Alt-T.
Enter the following: "sudo pico /etc/gdm3/custom.conf" 
 (Then Scroll Down, Down Arrow Key)
Uncomment (remove the hash symbol) from the line "#WaylandEnable=false" (Delete #)
Save your changes and exit pico. (CTRL "X")

Reboot.

If you want to re arrange the GRUB their is an Excellent GRUB Customizer within LINUX VOYAGER 18.04 that works well once you become familiar with it and remember to Save to the Master Boot Record.
GRUB Customizer can be Downloaded and Installed to UBUNTU 18.04 once you get it running.
Linux Mint 19 Xfce is extremely Slow nearly 10minutes to get to the Login Page on my Desktop but it looks like it Mint 19 has a Programming problem also.

Hopefully UBUNTU 18.10 will correct a few of these newly created software problems.
I nearly gave up on UBUNTU 18.04 and stuck to VOYAGER 18.04 but now I am Dual Booting with VOYAGER 18.04, MINT 19, UBUNTU 18.04
all are now working well.
[/LEFT]

---

### Post by fabio61 on 2018-10-04
You are great! It worked!

Thank you

---

### Post by fabio61 on 2018-10-04
And I will try the GRUB customizer

---

