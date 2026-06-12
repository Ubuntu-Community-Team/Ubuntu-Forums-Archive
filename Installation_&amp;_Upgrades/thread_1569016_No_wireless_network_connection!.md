---
title: "No wireless network connection!"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-09-06
I have been uninstalling, reinstalling, .... for about the past 14 hours and finally I realize I need help. First, I am trying to install the latest Ubuntu 10.04.1 (64-bit) on a Windows 7 laptop (HP Pavilion).

I did have 10.04 running for a few months on this laptop but when I recently upgraded to ver. .... 32-24  things started to go wrong. Suddenly, I could no longer even bootup Ubuntu ...32-24. But, I was able to use ...32-23 or ...32-21 which were also on my machine. Then in trying to fix ...32-24 all my installed versions of Ubuntu 10.04 became unbootable. I tried many suggestions (see my postings on this yesterday and today on the Ubuntu forum -- General help) .  

I realized that this was hopeless after many attempts. I could not bootup, even from my bootable Ubuntu CD. I then decided to just begin from scratch and install the latest downloadable Ubuntu --- I started with this early this morning. This went rather smooth; but, no matter how many reinstallations I did, I could never make a wireless connection to the network. Note, the same wireless hardware and settings were used as in the previous working versions of Ubuntu 10.04 and Windows 7 (on the same machine) --- I have not made any hardware changes. 

I am sending this message from my desktop PC which has Ubuntu 10.04 (32-bit) and again, I have carefully checked and verified that the setting for my wireless connection to the internet are identical for both (this desktop and my laptop). However, I am still unable to make a wireless network connection on my laptop!

Please --- I need some help on this. What can I do to get my wireless network working on my laptop with the latest download of Ubuntu 10.04.1? It could be that this latest download of Ubuntu 10.04.1 does not have the necessary drivers/software for the wireless network. But, it was ok in the previous downloadable --- I had been using it for a couple of months with no problems at all. Is it possible to reinstall 10.04 vers. ...32-23 rather that 10.04.1 vers. ...32-24? I could not find this on the Web.

I can provide screen snapshots and other information (log files, etc.) if needed. HELP!

---

### Post by Tracy177 on 2010-09-06
May Ubuntu be with you:)
 
 
there is a button in your laptop to switch you wifi off and on.
 
press it and try to connect to internet 
 
if it still doesnt work  type in terminal dmesg
and if your wifi card is inside your laptop lspci paste it over here.

---

### Post by virsto on 2010-09-06
> **Tracy177 said:**
> May Ubuntu be with you:)
 
 
there is a button in your laptop to switch you wifi off and on.
Yes, this is ok --- checked this earlier (but thanks for the reminder) :)
 
press it and try to connect to internet 
 
if it still doesnt work  type in terminal dmesg
and if your wifi card is inside your laptop lspci paste it over here.

It exceeds the 19.5KB limit, so I will now attach the first half and then send the second half in a few minutes.

---

### Post by virsto on 2010-09-06
> **virsto said:**
> It exceeds the 19.5KB limit, so I will now attach the first half and then send the second half in a few minutes.

And now for the second part...,

---

### Post by Tracy177 on 2010-09-06
> **virsto said:**
> It exceeds the 19.5KB limit, so I will now attach the first half and then send the second half in a few minutes.
 
 
can you see any networks in network mgr ?
 
could you post lspci ?
 
did you press the wifi button in your laptop ?

---

### Post by virsto on 2010-09-06
> **Tracy177 said:**
> May Ubuntu be with you:)
 
 
there is a button in your laptop to switch you wifi off and on.
 
press it and try to connect to internet 
 
if it still doesnt work  type in terminal dmesg
and if your wifi card is inside your laptop lspci paste it over here.

And here is what I get from lspci (desktop 32-bit that is ok):

root@virgil-desktop:/home/virgil# lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
06:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
07:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
root@virgil-desktop:/home/virgil# 

********************************************
Here is what I get from lspci on my LapTop:

virgil@ubuntu:/$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
virgil@ubuntu:/$

---

### Post by virsto on 2010-09-06
And thanks very much Tracy177.

---

### Post by Tracy177 on 2010-09-06
> **virsto said:**
> And thanks very much Tracy177.
 
 
could you paste dmesg from your laptop ? dont attach it 
 
 
also tell me if you can see any networks in network manager?
 
did you try to press the button switch for your wifi in your laptop ?
 
u have broadcom card so it should work

---

### Post by virsto on 2010-09-06
> **Tracy177 said:**
> could you paste dmesg from your laptop ? dont attach it 
Ok, I will try but it is large --- the raison d'etre for the attachments.

 Just as I thought --- too large!

 
also tell me if you can see any networks in network manager?

Well, I tried System -> Administration -> Network Tools but I am not sure that I can tell if it sees any networks.
 
did you try to press the button switch for your wifi in your laptop ?
Yes, I have toggled it on/off many times --- the is not the problem
 
u have broadcom card so it should work
But it doesn't work and it did on 10.04   vers. 32-24.

Hope this helps.

---

### Post by virsto on 2010-09-06
I  have to be away for about 30 minutes --- be back as soon as I can to continue with this line...

---

### Post by virsto on 2010-09-06
Ok I am back Tracy177...
I could send parts of the dmesg output --- just tell me what you are looking for in it.

---

### Post by Tracy177 on 2010-09-06
> **virsto said:**
> Ok I am back Tracy177...
I could send parts of the dmesg output --- just tell me what you are looking for in it.
 
 
there is dmesg is info about wifi firmware if firmware is missing you will see in dmesg request for wifi firmware.
 
 
second i asked you if you tried to press wifi switch button in your laptop or not ?
 
maybe everything you need to do is to switch you wifi on.

---

### Post by virsto on 2010-09-06
> **Tracy177 said:**
> there is dmesg is info about wifi firmware if firmware is missing you will see in dmesg request for wifi firmware.

 
 
second i asked you if you tried to press wifi switch button in your laptop or not ?
 
maybe everything you need to do is to switch you wifi on.

1. I searched for 'wifi' and 'firmware' --- no hits on these strings.
2. I believe that I have stated that the switch for wifi is on --- on my laptop it is a beacon with blue backlighting when it is on. It changes to red when it is off. I never leave this off and I have toggled it on/off many, many times --- no effect! So I do not believe this line needs to be pursued further.

---

### Post by realzippy on 2010-09-06
No driver offered in System/Administration/Hardware drivers?

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> No driver offered in System/Administration/Hardware drivers?

System -> Administration -> Hardware Drivers give the followin:

[B]Downloading package indexes failed, please check 
your network status. Most drivers will not be available.[/B]

Then if I continue (hit close button)

There is a search of hardware drivers but this gives the message:

 **No proprietary drivers are in use on this system.**

---

### Post by virsto on 2010-09-06
Please remember that I do have access to the Web (for downloading drivers) on the same machine and also on my Desktop (which this is coming from).

---

### Post by realzippy on 2010-09-06
suggest to install (or reinstall if already installed) the packages:

[B]bcmwl-kernel-source
   broadcom-sta-common
   broadcom-sta-source[/B]


What does 

```
sudo apt-get update
```


say?

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> suggest to install (or reinstall if already installed) the packages:

[B]bcmwl-kernel-source
   broadcom-sta-common
   broadcom-sta-source[/B]


What does 

```
sudo apt-get update
```
say?

I will like very much to install these --- where do I get them, and how are they installed?

And here is what I get from ```
sudo apt-get update
```

```
virgil@ubuntu:~$ sudo -s
[sudo] password for virgil: 
root@ubuntu:~# sudo apt-get update
Err http://us.archive.ubuntu.com lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:~# 

```

---

### Post by realzippy on 2010-09-06
Your not-running wifi is not the problem,it is a symptom.
Do you have synaptic or software center opened when running "sudo apt-get update"  ?

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> Your not-running wifi is not the problem,it is a symptom.
Do you have synaptic or software center opened when running "sudo apt-get update"  ?

Sorry for the delay --- I am using a USB stick to tranfer files between my laptop and desktop...

Here is the results of the "sudo apt-get update" again,

```
sudo apt-get update
Err http://us.archive.ubuntu.com lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:~# 

```

and here is info on my controller:

```
virgil@ubuntu:~$ lspci -vvnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
virgil@ubuntu:~$ 

```

---

### Post by realzippy on 2010-09-06
The problem is:
dpkg (your package manager) cannot reach the server
[I]Could not resolve 'us.archive.ubuntu.com
[/I]
Unlikely the server is down,but you can sort this out by changing to another server:

Open synaptic packet manager,settings/repositories and
change the server to some other.Then close synaptic and
run again:

**sudo apt-get update**

Note:no need to become "root" as you did formerly,"sudo" makes you root temporarily...

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> suggest to install (or reinstall if already installed) the packages:

[B]bcmwl-kernel-source
   broadcom-sta-common
   broadcom-sta-source[/B]


What does 

```
sudo apt-get update
```


say?
Ok I have download these 3 packages --- should I go ahead with their installation?

---

### Post by virsto on 2010-09-06
But, how can I reach a server from my laptop Ubuntu when I have no connection to the internet on my laptop Ubuntu?

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> The problem is:
dpkg (your package manager) cannot reach the server
[I]Could not resolve 'us.archive.ubuntu.com
[/I]
Unlikely the server is down,but you can sort this out by changing to another server:

Open synaptic packet manager,settings/repositories and
change the server to some other.Then close synaptic and
run again:

**sudo apt-get update**

Note:no need to become "root" as you did formerly,"sudo" makes you root temporarily...

I forgot to quote --- How can I use my package manager to get to a server when I have no connection to the network?

---

### Post by realzippy on 2010-09-06
Please do not install the packages when you downloaded them from another computer.
As I said:You have a problem with your dpkg,this leads to the problem with your wifi.
Please let`s do it step by step.
So,I thought your laptops wifi does not work,but is also connected to the internet with a cable... right?

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> Please do not install the packages when you downloaded them from another computer.
As I said:You have a problem with your dpkg,this leads to the problem with your wifi.
Please let`s do it step by step.
So,I thought your laptops wifi does not work,but is also connected to the internet with a cable... right?

I better go over this again.
1. I only have a wireless connection to all my computers --- I have no cable!
2. I can connect to the web via the same wireless box on three of my OSs; but, it is the 4th one (Ubuntu on my laptop) that I can not make a connection with at all.
3. I can download *.deb files (or any other files) from any of the other 3 machines and move them to the laptop (as I have down with the 3 files that you mentioned). I just copy them to a USB stick, then transport the USB stick, and copy them to the laptop.

Hope this clarifies my situation.

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> Please do not install the packages when you downloaded them from another computer.
As I said:You have a problem with your dpkg,this leads to the problem with your wifi.
Please let`s do it step by step.
So,I thought your laptops wifi does not work,but is also connected to the internet with a cable... right?

Why should I not move the *.deb files that I have downloaded on another machine to my laptop?

---

### Post by realzippy on 2010-09-06
*Hope this clarifies my situation*

Yes,thanks.

So try to install the downloaded .deb files.If
install fails `cause of missing dependencies packages,you had to download and install them also.
If this worked,reboot and pray.
If not,you should get a cable for that particular machine...

*Why should I not move the *.deb files that I have downloaded on another machine to my laptop?*

...because of eventually missing dependency packages...

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> Please do not install the packages when you downloaded them from another computer.
As I said:You have a problem with your dpkg,this leads to the problem with your wifi.
Please let`s do it step by step.
So,I thought your laptops wifi does not work,but is also connected to the internet with a cable... right?

I do not understand this --- I can see no problem with dpkg. IMHO the problem is  that I am unable to connect my laptop to the network, which is the underlying reason for the error messages displayed.

---

### Post by realzippy on 2010-09-06
> **virsto said:**
> I do not understand this --- I can see no problem with dpkg. IMHO the problem is  that I am unable to connect my laptop to the network, which is the underlying reason for the error messages displayed.

That is right.I thought that machine was connected with a cable also..

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> *Hope this clarifies my situation*

Yes,thanks.

So try to install the downloaded .deb files.If
install fails `cause of missing dependencies packages,you had to download and install them also.
If this worked,reboot and pray.
If not,you should get a cable for that particular machine...

*Why should I not move the *.deb files that I have downloaded on another machine to my laptop?*

...because of eventually missing dependency packages...

Ok, I tried to install all three of them; but, only one of them installed (broad-sta-common). There were unsatisfied dependencies --- as you said there would be.

I do not understand how a version of Ubuntu be released when there are such problems.

---

### Post by realzippy on 2010-09-06
Generally it is "dangerous" to run kernel updates,especially when
using a driver (like your broadcom wlan driver) that needs the kernel sources..
Your "older" kernel/wlan still works?

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> Generally it is "dangerous" to run kernel updates,especially when
using a driver (like your broadcom wlan driver) that needs the kernel sources..
Your "older" kernel/wlan still works?

I believe I answered this question in my very wordy firs posting about this problem.

I am rather disappointed with Ubuntu updates --- this not the first time I have experienced such irritating problems. I have always been a believer (as I tell my students) of keeping up-to-date; but, I am beginning to have my doubts about this philosophy when it comes to Ubuntu updates (esp. for 64-bit platforms).

---

### Post by virsto on 2010-09-06
> **realzippy said:**
> Generally it is "dangerous" to run kernel updates,especially when
using a driver (like your broadcom wlan driver) that needs the kernel sources..
Your "older" kernel/wlan still works?

I can try to get a cable tomorrow and see if I can connect and then make the necessary downloads; but, I am not very optimistic.:(

Do you have any other suggestions/ideas about the solution to the problem? 
I have now being working more or less continuously (except for some short breaks) for over 24 hours, and fatigue is setting in rapidly --- better try to get some rest and make a fresh attack on this tomorrow (it is now 21:12 in Stockholm).

Thanks for your efforts "realzippy" and Tracy177. :)
Have a good day! and hope to make contact with you again tomorrow --- I have not given up yet.

---

### Post by realzippy on 2010-09-06
"I believe I answered this question in my very wordy firs posting about this problem."
Yes or No would have been shorter...you said it boots,not that it boots
*and* can wlan.Thats a difference...anyway I can feel with you,good idea to have a break.
Other solutions:
Manually installing a deb file of course is possible,but can lead to annoying situations: A depends on B,which needs C,D,F,G and when you at last installed F you recognize that G depends on A.You see the potencial
fun?Thats why dpkg & sons exist.Linux package management without internet is a No-Go..
Only other solution besides the LAN cable would be a USBwlan stick (I got one from the supermarket for 10 euro,some work out of the box) but I guess if you had one,you already used it.
"I am rather disappointed with Ubuntu updates" yes,after 3 years of linux I have learned that it is a very good idea to disable update-notifier and
check updates manually twice a month.Generally bugs are eliminated after
a few days;*if* your problem is broadcom-sta related then it is broadcom`s job unless they free the source-code.Compared to others they make a good job,btw.
Back to topic,tomorrow's attack:
```
sudo apt get update && sudo apt-get upgrade
```
Reboot and check *HardwareDrivers* again for broadcomSTA driver to install.If still no luck:
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Reboot and check *HardwareDrivers* again for broadcomSTA driver to install.
Godnight,back tomorrow.

---

### Post by virsto on 2010-09-07
> **realzippy said:**
> "I believe I answered this question in my very wordy firs posting about this problem."
Yes or No would have been shorter...you said it boots,not that it boots
*and* can wlan.Thats a difference...anyway I can feel with you,good idea to have a break.
Other solutions:
Manually installing a deb file of course is possible,but can lead to annoying situations: A depends on B,which needs C,D,F,G and when you at last installed F you recognize that G depends on A.You see the potencial
fun?Thats why dpkg & sons exist.Linux package management without internet is a No-Go..
Only other solution besides the LAN cable would be a USBwlan stick (I got one from the supermarket for 10 euro,some work out of the box) but I guess if you had one,you already used it.
"I am rather disappointed with Ubuntu updates" yes,after 3 years of linux I have learned that it is a very good idea to disable update-notifier and
check updates manually twice a month.Generally bugs are eliminated after
a few days;*if* your problem is broadcom-sta related then it is broadcom`s job unless they free the source-code.Compared to others they make a good job,btw.
Back to topic,tomorrow's attack:
```
sudo apt get update && sudo apt-get upgrade
```Reboot and check *HardwareDrivers* again for broadcomSTA driver to install.If still no luck:
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Reboot and check *HardwareDrivers* again for broadcomSTA driver to install.
Godnight,back tomorrow.

Ok, I am back on the problem --- and yes it is not solved yet!
Let me summarize how things stand.

1. Unable to connect to the internet via a wireless system on LapTop running Ubuntu 10.04.1 (vers. ...32-24), 64-bit

2. Can connect to the internet using the **same wireless system on the same LapTop running Windows 7** **(64-bit**)

3. Can connect to the internet using the same wireless system on a DeskTop running Ubuntu 10.04 (vers. ...32-24), 32-bit.

4. Connected to the internet via a cable on LapTop running Ubuntu (as in 1.)
   -- updated all packages using Synaptic Package Manager (no error/failures reported)
   -- installed latest (I believe)
       [B]bcmwl-kernel-source
       broadcom-sta-common
       broadcom-sta-source[/B]
      all dependencies were resolved and no errors/failures reported

   The output of System -> Administration -> Hardware Drivers is attached.

4. Then, followed your suggestion and executed (while connected with cable):

      ```
sudo apt-get update && sudo apt-get upgrade 
```      

    Output attached.

There is an animated icon that now continually shows that it is trying to connect via the
wireless but the connection is never made. I have checked, and checked, and... character by character the information needed for the wireless and IT IS CORRECT! The identical information works on 3 other operating systems (Windows Vista, Windows 7 and Ubuntu 10.04 (vers. ... 32-24), 32-bit). I have screens shots from the two Ubuntu systems if you would like to check this yourself.

**Still unable to use my wireless internet system on Ubuntu 10.04.1 (vers. ...32-24), 64-bit.**

Note, I can now switch between a direct cable connection and wireless connection; but, this can take 3 to 4 minutes.

What next?

---

### Post by realzippy on 2010-09-07
Ok.at least you could connect through WLAN booting the older Kernel.So the laptop is usable;**any** reason why you have to run the new kernel**?**If not,I suggest to  run the working one.

Anyway,
in the last time I saw certain threads concerning misbehaving *network-manager*,*wicd* as alternative worked.

To see status of your wlan run:

```
iwconfig
```

..might give a clue.


Edit:
Does unloading and reloading modules help: (?)

```
sudo modprobe -r b44 b43 ssb wl
sudo modprobe wl
sudo modprobe b44 ssb
```

---

### Post by virsto on 2010-09-07
Ok,
I just came back online --- I will now look at your suggestions and see what I can do ... get back to you with the results soon.

--V

---

### Post by virsto on 2010-09-07
Opphs .. I have not changed kernels --- I am still trying to get Ubuntu 10.04.1 (vers. ... 32-24) 64-bit working as I have from the beginning. This is the only one that I found at the Ubuntu download URL.
I would like to return to vers. ... 32-23 but have not found this version for download and installation.

--V

---

### Post by virsto on 2010-09-07
> **realzippy said:**
> Ok.at least you could connect through WLAN booting the older Kernel.So the laptop is usable;**any** reason why you have to run the new kernel**?**If not,I suggest to  run the working one.

Anyway,
in the last time I saw certain threads concerning misbehaving *network-manager*,*wicd* as alternative worked.

To see status of your wlan run:

```
iwconfig
```..might give a clue.


Edit:
Does unloading and reloading modules help: (?)

```
sudo modprobe -r b44 b43 ssb wl
sudo modprobe wl
sudo modprobe b44 ssb
```

I have attached the results from both machines running Ubuntu for comparison.

I have also attached the results of trying this code (I believe that the last modprobe cmd is incorrect). 

--V

---

### Post by virsto on 2010-09-07
For some reason one of the attachments was not attached to my reply --- try again.

---

### Post by virsto on 2010-09-07
[QUOTE=realzippy;9816167]Ok.at least you could connect through WLAN booting the older Kernel.So the laptop is usable;**any** reason why you have to run the new kernel**?**If not,I suggest to  run the working one.

Anyway,
in the last time I saw certain threads concerning misbehaving *network-manager*,*wicd* as alternative worked.

To see status of your wlan run:

```
iwconfig
```..might give a clue.


And something else to look at. I have attached two screen shots, one from the problem machine (LapTop) and the other from the ok machine (Desktop). Can you tell which one is from the LapTop and and which is from the DeskTop?

I have attached these because when one looks at the output from iwconfig, the LapTop is not picking up the SSID (B2_private_56).

--V

---

### Post by realzippy on 2010-09-07
You have different passwords...

91909190F  and

919091904F ??

---

### Post by virsto on 2010-09-07
YES! Very stupid of me. But, now I am unable to recover from the modprobe cmds that I executed; i.e., it does not even try to connect now.

--V

---

### Post by realzippy on 2010-09-07
So restart.BTW,the older kernel should be still available if you did not deinstall them manually.Press "ESC" when booting to show all available kernels...

---

### Post by virsto on 2010-09-07
EUREKA!!! Connection has been made ---- I apologize for my very stupid mistake. You would not believe how many times I checked this and missed it --- must be old age dementia setting in on me.

Thanks very very much for your tenacity on this problem. I will try to summarize how this problem was solved and post it with a status of "SOLVED".

Have a good day realZippy!

---

### Post by realzippy on 2010-09-07
You are welcome.Glad you made it..have fun!

---

### Post by virsto on 2010-09-07
Finally with the very useful inputs and perseverance of realZippy this problem has been solved.

**It seems that a connection to the Internet on the machine with the problem is required! This is important.** In my case, I made a direct cable connection to the internet from my laptop. Once I made this direct cable connection and was online, I then performed the following:

1. System -> Administration -> Update Manager and then perform updates of everything offered.

2. Download:
    
    [B]bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb
    broadcom-sta-source_5.60.48.36-3_all.deb
    broadcom-sta-common_5.10.91.9.3-3_all.deb[/B]

    and install them. There should be no errors/failures and all dependencies resolved.

    You can now remove the direct cable connection. Note, the wireless device is automatically activated on my laptop when there is no direct cable connection.

3. Define the parameters for the wireless connection. I used System -> Preferences -> Network Preferences, to accomplish this. Be very careful here (I wasn't :()

4. Reboot and... the-tha-tha-that-that's all folks! :D

Have a good day!

---

