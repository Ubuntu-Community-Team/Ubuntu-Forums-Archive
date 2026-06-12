---
title: "Ubuntu 10.10, delete kernel by accident!!!"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by dehiker on 2011-02-16
***Some Index to the Solutions***
  1. **Install kernel: **see #2 (I make it with kernel file in /var/cache/apt/archive)
   
  After installation of kernel, there may be some problems:
  2. **Win7 disappear in the grub**: see the content below "Not see Windows 7:    ", #6
  3. **Cannot connect to the network**: see #8.

> While trying to remove old kernels, I delete all of them by accident!!!  There're now only two "Memory test" and a "win7" in the grub.:sad:

Since there's lots of data on the disk, and I have no idea how to keep  them safe if reinstalling the system, so I really hope not to do that.

Then I enter Ubuntu 10.10 cd, and **sudo apt-get install** a kernel (*three 2.6.35 or so, of which two with "generic" and not, and one with "image"*), everything seems OK. And I guess what I did really changed the system, since the *source_list* file in the **/etc/apt/** did be changed. But the grub still has only 3 options.

What else should I do to add the newly installed kernel to the grub? Or What should I do while I delete all kernels by accident?

Hope I have put my problem expicitly, and look forward for you help!

dehiker

---

### Post by amsterdamharu on 2011-02-16
A chroot might work, chroot means that when you start a system you change the root file system. For example you started from a live CD but you change the root "/" to where your ubuntu is installed.

Lets say your ubuntu is installed on /dev/sda2 then you can try the following commands:

```
sudo mount /dev/sda2 /mnt
sudo cp /etc/resolv.conf /mnt/etc/
sudo cp /etc/hosts /mnt/etc/
sudo mount --bind /dev/ /mnt/dev
sudo chroot /mnt
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C
dbus-uuidgen > /var/lib/dbus/machine-id
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
# now you're root "/" is on /dev/sda2, try installing the kernel
apt-get update
apt-get install linux-image-2.6.32-26-generic
update-initramfs -cv
update-grub
```

I had to do a little guesswork here since I never had to do this before but this should be about it. Don't know if you get some fstab error warning (like can't find root).

Now you need to clean up some stuff and unmount the mounted partitions:
```
rm /etc/resolv.conf
rm /etc/hosts
rm /var/lib/dbus/machine-id
rm /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl
umount /proc # if this doesn't work try umount -lf /proc
umount /sys
umount /dev/pts
exit
sudo umount /mnt
```

And you can reboot to see if it worked.

If it didn't please post the output of the terminal here:
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy the commands and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by dehiker on 2011-02-16
Thank you so much for prompt reply, amsterdamharu!

But I have a problem. it seems I have no[COLOR=red] /etc/resolv.conf[/COLOR] file when I started from live CD. And I find there's only a folder[COLOR=blue] /etc/resolvconf/[/COLOR], in which there is a file [COLOR=blue]/update-libc.d/avahi-daemon[/COLOR].

So, how could I go forward? Any ideas?
 
Thank you again for your attention!

---

### Post by amsterdamharu on 2011-02-16
The resolv.conf should contain the dns server, you can leave it out and not copy it if Internet still works.

I don't have the 10.10 live cd so don't really know why it's missing. One great thing in Linux is when you finally figure out where some information is stored they go around and change it. (+sarcasm.. Oh give me back my registry).

Later you need to do the apt-get install, that will try to connect to the Internet unless you still have the files in your /var/cache/apt/archive folder which is likely and then you don't even need an Internet connection.

---

### Post by dehiker on 2011-02-17
Thank you a lot, amsterdamharu! I am so happy to see my ubuntu coming back!
 
But here are some other problems:
[COLOR=darkred]Firstly, it seems I have some difficulty in connecting to the network.[/COLOR]
[COLOR=darkred]Secondly, after the process, I couldn't see win7 in the grub anymore.[/COLOR]
Maybe I forgot to do something important?
 
After chroot, I install the kernel with the file in /var/cache/apt/archive, so it was finished without network. And another difference is the following command:
```
 
update-initramfs -cv -k all # the command ask for some option, so I added "-k all"

```Then,
```
 
rm /etc/hosts
#rm /var/lib/dbus/machine-id # forgot to do this
#rm /sbin/initctl # also forgot
#dpkg-divert --rename --remove /sbin/initctl # also forgot
umount /proc
umount /sys
umount /dev/pts
exit
sudo umount /mnt

```After reboot, I found the problems mentioned above. Do you have any ideas?

---

### Post by amsterdamharu on 2011-02-18
I don't think not removing the files would be a big deal. 
Not having Network:
Is it wireless/wired is it usb wireless or pci?
If it's wired network could you post the output of the following commands
```
sudo lspci -vv
cat /etc/networks
ifconfig -a
sudo dhclient
```
The output of lspci is very long, please post only the part that gives details about your network card.


Not see Windows 7:
If you boot up from harddisk and execute the following command:
```
sudo update-grub
```Does Windows come back in the boot menu?
If not could you post the output of boot info script
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Copy it to your Desktop (it usually is in Downloads).
Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script*
```
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
There should be a file on your Desktop named RESULTS.txt please post the content of this file here using &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by dehiker on 2011-02-18
After executing command
```
sudo update-grub

```win7 is back!!
 
About the network, yes, it's wired network. And I hope the lspci's content I post is what you need. Thank you again, amsterdamharu!
 
**[COLOR=darkred]sudo lspci -vv[/COLOR]**
>  
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Subsystem: Device 1a3b:1089
Physical Slot: 1
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 17
Region 0: Memory at d6000000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [40] Power Management version 3
Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
Address: 00000000 Data: 0000
Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
MaxPayload 128 bytes, MaxReadReq 512 bytes
DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
ClockPM- Surprise- LLActRep- BwNot-
LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
DevCap2: Completion Timeout: Not Supported, TimeoutDis+
DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
Compliance De-emphasis: -6dB
LnkSta2: Current De-emphasis Level: -6dB
Capabilities: [100 v1] Advanced Error Reporting
UESta: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
UEMsk: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
CESta: RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
CEMsk: RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
Capabilities: [140 v1] Virtual Channel
Caps: LPEVC=0 RefClk=100ns PATEntryBits=1
Arb: Fixed- WRR32- WRR64- WRR128-
Ctrl: ArbSelect=Fixed
Status: InProgress-
VC0: Caps: PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
Arb: Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
Ctrl: Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
Status: NegoPending- InProgress-
Capabilities: [160 v1] Device Serial Number 00-15-17-ff-ff-24-14-12
Capabilities: [170 v1] Power Budgeting <?>
Kernel driver in use: ath9k
Kernel modules: ath9k


**[COLOR=darkred]cat /etc/networks[/COLOR]**
> 
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0 

 
**[COLOR=darkred]ifconfig -a[/COLOR]**
>  
eth0 Link encap:Ethernet HWaddr bc:ae:c5:06:bb:5f 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:156 errors:0 dropped:0 overruns:0 frame:0
TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:11588 (11.5 KB) TX bytes:11588 (11.5 KB)
wlan0 Link encap:Ethernet HWaddr 48:5d:60:67:30:bc 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
 
 
**[COLOR=darkred]sudo dhclient[/COLOR]**
>  
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Listening on LPF/wlan0/48:5d:60:67:30:bc
Sending on LPF/wlan0/48:5d:60:67:30:bc
Listening on LPF/eth0/bc:ae:c5:06:bb:5f
Sending on LPF/eth0/bc:ae:c5:06:bb:5f
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 


---

### Post by amsterdamharu on 2011-02-18
The info is for your wireless, I am not sure if your wired network is up or not or if it has drivers. Looks like your wireless is working fine, or it should. They don't get an IP address when you ask for it with dhcp, are you connected to a router/modemrouter, directly through cable or connected to a dsl modem?

You could try this command:
```
sudo ifconfig eth0 up
```
And maybe try asking for an ip adress again:
```
sudo dhclient
```

---

### Post by dehiker on 2011-02-18
I'm so grateful to you, amsterdamharu!
After
```
sudo ifconfig eth0 up
sudo dhclient
```I could connect to the network now!!!

By the way, do you have any suggestions [COLOR=DarkRed]how I could improve my linux & ubuntu skills[/COLOR]? It seems I always have no idea when encountering some new problems. I'm eager to be an linux master like you, but don't know how to. Looking forward for your advices. :D

---

### Post by amsterdamharu on 2011-02-18
Reading solved threads might help. By no means am I a master, there are many times I have no idea what to do as well.

A good starting point would be to use google if you type the following:
site:ubuntuforums.org "some error you are getting"
site:help.ubuntu.com setup network
site:packages.ubuntu.com some driver you are looking for


About the chroot, I needed to customize live cd. A good article could be found here:
site:help.ubuntu.com customize live CD
The code is from that site. Chrooting means that you are running Linux and change the root partition. Root partition is the base of your filesystem not root as in root user. In root you have directories like home boot etc and others.
If you run a live CD session and would install a kernel it would only install in the live session, you needed it on your harddisk so I figured starting a live session and then chrooting to harddisk install would do the trick.
It works if you extract the live system squasfs (sort of a zipped filesystem) then chroot to it and install stuff.

I am happy it worked, hope your skills in Linux get really good but don't hesitate to ask anything on the forums here.

---

### Post by Melvin1981 on 2011-02-18
Hi! I removed old linux-images from Synaptic.

linux-image-2.6.35-22, 
linux-image-2.6.35-23, 
linux-image-2.6.35-24, 
linux-image-2.6.35-25.

So I removed all kernels except for linux-image-2.6.35-25.
Then I realizaed that grub don't have any other options to boot except for linux-image-2.6.35-22.
Thanks to your instructions I re-installed old linux-image.
Performed update-grub in Terminal.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done  

But still when booting system I have only oldest kernel.
Don't understand why.

But at least I have working system and I didn't need to reinstall OS for that. Next time I check twice 'uname -r' before cleaning!
Thank you Amsterdamharu. You are guru :P.

---

### Post by dehiker on 2011-02-19
I'm so grateful to you, amsterdamharu, for you great help and advices!:)

---

