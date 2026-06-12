---
title: "network-manager .8 broke USB 3G mobile broadband"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-08-07
As of today's update to network-manager, my Verizon UM150 USB 3G modem is no longer recognized.

Filed: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386)

I am wondering if the breakage is isolated to this device in particular or more broadly affecting other 3G units. Anyone else having issue with automobile broadband devices today?

---

### Post by jfernyhough on 2009-08-07
Try removing the connection from Network Manager settings. Configuration has most likely changed.

---

### Post by phenest on 2009-08-07
Mine neither. Huawei E169. It's not even showing as a USB device. :(

---

### Post by wayne_cat on 2009-08-07
> **phenest said:**
> Mine neither. Huawei E169. It's not even showing as a USB device. :(

Can you see the device with the command lsusb?

---

### Post by phenest on 2009-08-07
> **wayne_cat said:**
> Can you see the device with the command lsusb?

Yes I can.

---

### Post by wayne_cat on 2009-08-07
> **phenest said:**
> Yes I can.

That's good. Do you see something like this in /var/log/messages after plugging in?

```
Aug  8 00:24:18 macbook kernel: [ 4667.292114] usb 4-1: new full speed USB device using uhci_hcd and address 4
Aug  8 00:24:18 macbook kernel: [ 4667.448001] usb 4-1: configuration #1 chosen from 1 choice
Aug  8 00:24:18 macbook kernel: [ 4667.456855] option 4-1:1.0: GSM modem (1-port) converter detected
Aug  8 00:24:18 macbook kernel: [ 4667.456994] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
Aug  8 00:24:18 macbook kernel: [ 4667.460468] option 4-1:1.1: GSM modem (1-port) converter detected
Aug  8 00:24:18 macbook kernel: [ 4667.460598] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
 
```

---

### Post by phenest on 2009-08-07
No. Nothing.

---

### Post by phenest on 2009-08-07
Hang on. I think I'm mistaken. After unplugging and plugging in several times, it suddenly came alive.

---

### Post by tekstr1der on 2009-08-07
hmm.. maybe I'll try that ^^ then. This is what I get when I plug it in:
```

Aug  7 18:28:01 galvatron kernel: [  151.872162] usb 1-1: new high speed USB device using ehci_hcd and address 4
Aug  7 18:28:01 galvatron kernel: [  152.013395] usb 1-1: configuration #1 chosen from 1 choice
Aug  7 18:28:01 galvatron kernel: [  152.035453] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  7 18:28:01 galvatron kernel: [  152.090233] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
Aug  7 18:28:01 galvatron kernel: [  152.092389] usbcore: registered new interface driver cdc_acm
```

This is what I used to get back in the day (yesterday):
```

Aug  6 09:18:15 galvatron kernel: [ 4884.884070] usb 1-1: new high speed USB device using ehci_hcd and address 4
Aug  6 09:18:15 galvatron kernel: [ 4885.024440] usb 1-1: configuration #1 chosen from 1 choice
Aug  6 09:18:15 galvatron kernel: [ 4885.028109] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  6 09:18:15 galvatron kernel: [ 4885.103152] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
Aug  6 09:41:42 galvatron pppd[4213]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Aug  6 09:41:42 galvatron pppd[4213]: pppd 2.4.5 started by root, uid 0
Aug  6 09:41:42 galvatron pppd[4213]: Using interface ppp0
Aug  6 09:41:42 galvatron pppd[4213]: Connect: ppp0 <--> /dev/ttyACM0
Aug  6 09:41:42 galvatron kernel: [ 4885.105241] usbcore: registered new interface driver cdc_acm
Aug  6 09:41:42 galvatron kernel: [ 4885.105389] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug  6 09:41:42 galvatron kernel: [ 4890.030745] scsi 5:0:0:0: Direct-Access     PANTECH  Mass Storage     0001 PQ: 0 ANSI: 0 CCS
Aug  6 09:41:42 galvatron kernel: [ 4890.032983] sd 5:0:0:0: Attached scsi generic sg2 type 0
Aug  6 09:41:42 galvatron kernel: [ 4890.046538] sd 5:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by phenest on 2009-08-07
Although, it won't work as USB storage.

---

### Post by wayne_cat on 2009-08-07
> **phenest said:**
> No. Nothing.

so you don't have these 2 devices 

```
root@macbook:/etc/udev/rules.d# ls /dev/*USB*
/dev/ttyUSB0  /dev/ttyUSB1
root@macbook:/etc/udev/rules.d# 
```

---

### Post by jfernyhough on 2009-08-07
Did modemmanager get installed?

---

### Post by tekstr1der on 2009-08-07
> **jfernyhough said:**
> Try removing the connection from Network Manager settings. Configuration has most likely changed.

Did that. Now the connection is just gone. No new connection is detected.


[QUOTE=jfernyhough]Did modemmanager get installed? [/QUOTE]

No modemmanager here. Looks like that package is recently updated. Should that have been a dependency of the recent network-manager update?

---

### Post by wayne_cat on 2009-08-07
> **tekstr1der said:**
> Did that. Now the connection is just gone. No new connection is detected.




No modemmanager here. Looks like that package is recently updated. Should that have been a dependency of the recent network-manager update?

I have removed modemmanger and network manager to test it 

```
root@macbook:~# apt-get install network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  modemmanager network-manager-gnome
The following NEW packages will be installed:
  modemmanager network-manager network-manager-gnome
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/874kB of archives.
After this operation, 7111kB of additional disk space will be used.
Do you want to continue [Y/n]? 


```modemmanger is a dependency of network manager

---

### Post by jfernyhough on 2009-08-07
> **tekstr1der said:**
> No modemmanager here. Looks like that package is recently updated. Should that have been a dependency of the recent network-manager update?In Synaptic on a 'mark all upgrades' it wanted to install modemmanager, so I think it's important. :)

As an aside, I haven't yet upgraded to 0.8; I'm waiting for pptp and openvpn plugins. ;)

---

### Post by tekstr1der on 2009-08-07
Okay, don't know why aptitude didn't pick up on that in the first place. Installed modemmanager, rebooted and now...what a tease! When I plug in the modem, network applet sits and spins with both lights green, but never fully connects. I get an IP and DNS, but can't resolve any external addresses. Log is showing:
```

Aug  7 20:05:10 galvatron kernel: [  181.293011] usb 1-1: new high speed USB device using ehci_hcd and address 4
Aug  7 20:05:10 galvatron kernel: [  181.432424] usb 1-1: configuration #1 chosen from 1 choice
Aug  7 20:05:15 galvatron kernel: [  181.436706] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  7 20:05:15 galvatron kernel: [  181.556943] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
Aug  7 20:05:15 galvatron kernel: [  181.559049] usbcore: registered new interface driver cdc_acm
Aug  7 20:05:15 galvatron kernel: [  181.559618] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug  7 20:06:22 galvatron pppd[3574]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Aug  7 20:06:22 galvatron pppd[3574]: pppd 2.4.5 started by root, uid 0
Aug  7 20:06:22 galvatron pppd[3574]: Using interface ppp0
Aug  7 20:06:22 galvatron pppd[3574]: Connect: ppp0 <--> /dev/ttyACM0
Aug  7 20:06:22 galvatron pppd[3574]: local  IP address 75.195.XXX.XXX
Aug  7 20:06:22 galvatron pppd[3574]: remote IP address 66.174.XXX.XXX
Aug  7 20:06:22 galvatron pppd[3574]: primary   DNS address 66.174.95.44
Aug  7 20:06:22 galvatron pppd[3574]: secondary DNS address 66.174.92.14
```

So close! Tried plugging in in multiple times with no change. One difference I am noting was that previously, when working prior to update today, it showed up as Automobile Broadband connection and connected automatically. Now it showed up as NEW mobile broadband connection and made me select Verizon.

---

### Post by wayne_cat on 2009-08-07
> **tekstr1der said:**
> Okay, don't know why aptitude didn't pick up on that in the first place. Installed modemmanager, rebooted and now...what a tease! When I plug in the modem, network applet sits and spins with both lights green, but never fully connects. I get an IP and DNS, but can't resolve any external addresses. Log is showing:
```

Aug  7 20:05:10 galvatron kernel: [  181.293011] usb 1-1: new high speed USB device using ehci_hcd and address 4
Aug  7 20:05:10 galvatron kernel: [  181.432424] usb 1-1: configuration #1 chosen from 1 choice
Aug  7 20:05:15 galvatron kernel: [  181.436706] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  7 20:05:15 galvatron kernel: [  181.556943] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
Aug  7 20:05:15 galvatron kernel: [  181.559049] usbcore: registered new interface driver cdc_acm
Aug  7 20:05:15 galvatron kernel: [  181.559618] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug  7 20:06:22 galvatron pppd[3574]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Aug  7 20:06:22 galvatron pppd[3574]: pppd 2.4.5 started by root, uid 0
Aug  7 20:06:22 galvatron pppd[3574]: Using interface ppp0
Aug  7 20:06:22 galvatron pppd[3574]: Connect: ppp0 <--> /dev/ttyACM0
Aug  7 20:06:22 galvatron pppd[3574]: local  IP address 75.195.XXX.XXX
Aug  7 20:06:22 galvatron pppd[3574]: remote IP address 66.174.XXX.XXX
Aug  7 20:06:22 galvatron pppd[3574]: primary   DNS address 66.174.95.44
Aug  7 20:06:22 galvatron pppd[3574]: secondary DNS address 66.174.92.14
```So close! Tried plugging in in multiple times with no change. One difference I am noting was that previously, when working prior to update today, it showed up as Automobile Broadband connection and connected automatically. Now it showed up as NEW mobile broadband connection and made me select Verizon.

please connect again post the result from

```
cat /etc/resolv.conf
```

---

### Post by tekstr1der on 2009-08-07
```
:~$ cat /etc/resolv.conf
nameserver 66.174.95.44
nameserver 66.174.92.14

```

Same DNS nameservers I was getting from this connection when it was working previously. Not sure what the holdup is at the end to complete the connection?

---

### Post by tekstr1der on 2009-08-07
Also, a bit of a discrepancy here:
```
:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.193.XXX.XXX  P-t-P:66.174.121.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:97 (97.0 B)
```

So, it looks like I'm all hooked up, but wait...

```
:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: ttyACM0  [Verizon connection] ----------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            cdc_acm
  State:             connecting (getting IP configuration)
  Default:           no

  Capabilities:

```

Not so much then.

---

### Post by kylea on 2009-08-08
I am getting the same behaviour with my Huawei E220 connecting to Optus 3G

This is with Karmic 9.10 64bit Alpha 3. Fully patched

Network Manager just spins around and never completes the connection.

cat /etc/resolv.conf
nameserver 61.88.88.88
nameserver 61.88.88.88
# Generated by NetworkManager

ifconfig ppp0

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:114.73.zz.zzz  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:435 (435.0 B)  TX bytes:257 (257.0 B)

- Device: ttyUSB0  [Optus 3G] --------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connecting (getting IP configuration)
  Default:           no

  Capabilities:

I'll log a bug report

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/410634](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/410634)

---

### Post by phenest on 2009-08-08
> **wayne_cat said:**
> so you don't have these 2 devices 

```
root@macbook:/etc/udev/rules.d# ls /dev/*USB*
/dev/ttyUSB0  /dev/ttyUSB1
root@macbook:/etc/udev/rules.d# 
```

Yes. It seems to be recognised now.

> **kylea said:**
> I am getting the same behaviour with my Huawei E220 connecting to Optus 3G

This is with Karmic 9.10 64bit Alpha 3. Fully patched

Network Manager just spins around and never completes the connection.

That's all mine does. Never connects.

---

### Post by oygle on 2009-08-08
Network Manager also broke my USB 3G mobile broadband connection in Jaunty - 9.04

Not impressed, older kernels don't work either.

At this stage I'd have to say Windows network is far superior to Network manager, at least XP can connect with the USB 3G dongle.

Oygle

---

### Post by kylea on 2009-08-08
Earlier version was perfect - XP was always painful to set up.

Ubuntu 9.04 worked perfectly as did the Karmic version before this one.

Patience will pay off with this.

---

### Post by phenest on 2009-08-08
I have now noticed that my stick is not recognised in Jaunty as a storage device. I don't have a memory card in it, but I seem to remember that this stick has a built in memory (read only) that has the drivers on it. That's how it worked in Windows and Intrepid (haven't used it in a while).

---

### Post by kylea on 2009-08-08
Mine did not either (recognise the storage) - don't realy need any of the stuff on the USB drive for installation as it handled by the kernel.

---

### Post by phenest on 2009-08-08
> **kylea said:**
> Mine did not either (recognise the storage) - don't realy need any of the stuff on the USB drive for installation as it handled by the kernel.

Quite true. But as it did work in Intrepid, this is a regression.

---

### Post by GeorgeVita on 2009-08-08
Hi, can you please post info (**uname -a**) of the NOT working kernel?

Thanks in advance,
George

**>>> EDIT:** OK I found it from the launchpad link (post#1) it is Ubuntu 2.6.31-5.24-generic

---

### Post by kylea on 2009-08-08
Downgrading to 0.7.1.git... versions works.


libnm-glib0_0.7.1.git.5.272c6a626-0ubuntu1~nm1_amd64.deb
libnm-util1_0.7.1.git.5.272c6a626-0ubuntu1~nm1_amd64.deb
network-manager_0.7.1.git.5.272c6a626-0ubuntu1~nm1_amd64.deb
network-manager-gnome_0.7.1.git.3.0461fff8-0ubuntu2~nm1_amd64.deb

---

### Post by GeorgeVita on 2009-08-08
[COLOR="Gray"]... updated to NM0.8, stucked also with my E169, connected using **wvdial**, reading post from **kylea** (thanks), downgrading again!
G[/COLOR]
**>>> UPDATE:** could not downgrade to 0.7.1 as 'force version' not functioning! Also faced some 'stucks'.
Removing **modemmanager** (purge or via synaptic) I solved also the '[system frozen]("http://ubuntuforums.org/showthread.php?t=1202430")' caused using my ZTE MF636 modem!

---

### Post by tekstr1der on 2009-08-08
@kylea - updated my original bug report with a link to yours as the symptoms have changed with the installation of the modemmanager package. Where did you get the 0.7.1.git deb's?

Also noticing a NASTY side effect from this bug. After attempting to connect with the network applet, I remove the device, the system freezes completely, sometimes with just a black screen and cursor. I must do a hard power reset to kill it and reboot.

I have been fortunate over the years, since starting with Slackware in 1997, never to have had my Linux OS completely freeze or crash. That lucky streak has ended so now I'll just have to tell people I've never had a *release* version of Linux crash!

---

### Post by GeorgeVita on 2009-08-11
As this problem still exists:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386)
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/410634](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/410634)

 and you cannot use your 3G modem with N/M., **how are you connecting?**
Using other type of connection (WiFi, Ethernet) or other methods for the 3G connection?

My methods:
a. with Huawei E169 using wvdial before trying to connect via N.M. (otherwise the /dev/ttyUSbx port is busy)
b. with ZTE MF636 using wvdial after purging modemmanager (with modemmanager /dev/ttyUSBx ports are looping created/disconnected)

Regards,
George

---

### Post by kylea on 2009-08-11
"how are you connecting?"

I have a Wireless ADSL connection as well as the Mobile Broadband.

I use the Mobile Broadband when I am away from the office so I can provide  support to my clients.

Modemmanager is uninstalled for me - I assume it will be required once a patch is made for the main problem

---

### Post by wayne_cat on 2009-08-11
You can still use the "old school method"

- create a profile with pppconfig
- connect from the command line with:       pon <profile name>
- disconnect from the command line with:   poff <profile name>

---

### Post by setherd on 2009-08-11
I've been looking for this bug!!! I was just about to post about it. I thought I was going crazy.
I can use wvdial, but this bug is annoying.

---

### Post by kylea on 2009-08-11
If you downgrade to 0.7.1.git.3 and .git.5 and Lock the versions you can use the Network Manager until its fixed.

---

### Post by setherd on 2009-08-11
> **kylea said:**
> If you downgrade to 0.7.1.git.3 and .git.5 and Lock the versions you can use the Network Manager until its fixed.

I'll probably just stick with wvdial till this gets fixed. it's an important one though I also get the system lockup if I remove my modem (CDU-680) while trying to connect with network manger.

---

### Post by GeorgeVita on 2009-08-11
> **kylea said:**
> If you downgrade to 0.7.1.git.3 and .git.5 and Lock the versions you can use the Network Manager until its fixed.

Please 'show' the method to downgrade as the 'force version' cannot be used from Synaptic.
Do we have to download the previous .deb package?

> **wayne_cat said:**
> You can still use the "old school method"
- create a profile with pppconfig
- connect from the command line with:       pon <profile name>
- disconnect from the command line with:   poff <profile name>

This will be my 'next lesson' as it seems 'hard to learn' for my 1 year Ubuntu & Linux experience!

Regards,
George

---

### Post by tekstr1der on 2009-08-12
> **kylea said:**
> If you downgrade to 0.7.1.git.3 and .git.5 and Lock the versions you can use the Network Manager until its fixed.

Did you download .debs for network-manager? If so what location where they obtained from. I found the following:

network-manager_0.7.1.git.5.272c6a626-0ubuntu1~nm1_i386.deb

from [https://launchpad.net/~network-manager/+archive/ppa/+sourcepub/689097/+listing-archive-extra](https://launchpad.net/~network-manager/+archive/ppa/+sourcepub/689097/+listing-archive-extra)

Is that the package I want? Need to have this working while awaiting a fix to be delivered.

---

### Post by taavikko on 2009-08-12
Previous version: [http://launchpadlibrarian.net/29884194/network-manager_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb](http://launchpadlibrarian.net/29884194/network-manager_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb)

If in need of older debs, search the source page,
[https://edge.launchpad.net/ubuntu/+source/network-manager/](https://edge.launchpad.net/ubuntu/+source/network-manager/)

---

### Post by tekstr1der on 2009-08-12
Thanks!

> **taavikko said:**
> If in need of older debs, search the source page,
[https://edge.launchpad.net/ubuntu/+source/network-manager/](https://edge.launchpad.net/ubuntu/+source/network-manager/)

Maybe I'm just really slow today, but all I'm seeing on the source page is the source and the diffs for each successive version. I don't see any .debs there

---

### Post by taavikko on 2009-08-12
> **tekstr1der said:**
> Thanks!



Maybe I'm just really slow today, but all I'm seeing on the source page is the source and the diffs for each successive version. I don't see any .debs there

Version History->Builds ${arch}->files produced from build

---

### Post by tekstr1der on 2009-08-12
I see the entire version history and links to the diffs. I cannot, for the life of me, find any reference to builds on the page. The only .debs I can see are the ones from the PPA listed under "other versions..." that I had linked to a few posts ago.

EDIT: Never mind, I am overtired and lacking observational skills today!

---

### Post by taavikko on 2009-08-12
> **tekstr1der said:**
> I see the entire version history and links to the diffs. I cannot, for the life of me, find any reference to builds on the page. The only .debs I can see are the ones from the PPA listed under "other versions..." that I had linked to a few posts ago.

Step one: source page
[https://edge.launchpad.net/ubuntu/+s...twork-manager/](https://edge.launchpad.net/ubuntu/+s...twork-manager/)

Step two: version history (long list in a center of the page)
[b]0.7.1.git.5.272c6a626-0ubuntu1
Superseded in karmic-release on 2009-08-07[/b]
click on the version number

Step three: Builds
[b]Builds

karmic sparc Successfully built (DONE)
karmic powerpc Successfully built (DONE)
karmic lpia Successfully built (DONE)
karmic ia64 Successfully built (DONE)
karmic i386 Successfully built (DONE)
karmic armel Successfully built (DONE)
karmic amd64 Successfully built (DONE)[/b]
choose(click) your architecture

Step four: Files produced drom the build
[B]Files produced from build

libnm-glib-dev_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb (103.6 KiB)
libnm-glib0_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb (61.6 KiB)
libnm-util-dev_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb (98.7 KiB)
libnm-util1_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb (101.4 KiB)
network-manager_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb (316.6 KiB)
network-manager-dev_0.7.1.git.5.272c6a626-0ubuntu1_i386.deb (6.2 KiB)[/B]

---

### Post by tekstr1der on 2009-08-12
@taavikko thanks for the walkthrough.

I removed modemmanager and downgraded network-manager and can verify that this returns the funcionality of my USB 3G modem. Hope to see some movement on the related bugs going toward Alpha 5.

---

### Post by GeorgeVita on 2009-08-13
Hi **tekstr1der**,
regarding your bug report: [https://bugs.launchpad.net/bugs/410634](https://bugs.launchpad.net/bugs/410634)
especially comment#11:> 1) Stop NetworkManager
2) run /usr/sbin/modem-manager --debug
3) Start NetworkManager
4) Plug in your modem
I am trying to get 'log info' but I faced:```
g@KKa4:~$ sudo /usr/sbin/modem-manager --debug

** (modem-manager:3669): WARNING **: Could not acquire the org.freedesktop.ModemManager service as it is already taken. Return: 3

```after stopping network-manager with: **sudo /etc/init.d/NetworkManager stop**

Can you help me skip this problem?

Thanks in advance,
George

---

### Post by svasie on 2009-08-13
I had a similar problem in Jaunty. When i plugged my 3G USB Dongle (Option), it was recognized only as USB storage and mounted as a new usb drive.


Ejecting (not unmounting) the drive makes Network Manager recognize the 3G modem and work ok.

Haven't tried it in Karmic.

Hope it helps.

---

### Post by tekstr1der on 2009-08-13
> **GeorgeVita said:**
> Hi **tekstr1der**,
regarding your bug report: [https://bugs.launchpad.net/bugs/410634](https://bugs.launchpad.net/bugs/410634)
especially comment#11:
I am trying to get 'log info' but I faced:```
g@KKa4:~$ sudo /usr/sbin/modem-manager --debug

** (modem-manager:3669): WARNING **: Could not acquire the org.freedesktop.ModemManager service as it is already taken. Return: 3

```after stopping network-manager with: **sudo /etc/init.d/NetworkManager stop**

Can you help me skip this problem?

Thanks in advance,
George

Run it without sudo.

```
/usr/sbin/modem-manager --debug
```

---

### Post by GeorgeVita on 2009-08-13
Hi **tekstr1der**, aprox. same results:```
g@KKa4:~$ /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ] 
g@KKa4:~$ /usr/sbin/modem-manager --debug

** (modem-manager:3056): WARNING **: Could not acquire the org.freedesktop.ModemManager service.
  Message: 'Connection ":1.84" is not allowed to own the service "org.freedesktop.ModemManager" due to security policies in the configuration file'
g@KKa4:~$ sudo wvdial
[sudo] password for g: 
--> WvDial: Internet dialer ...
```... possibly because I moved one step backwards to Alpha 4, I will test it later after upgrading it.

Thanks,
George

---

### Post by tekstr1der on 2009-08-13
@GeorgeVita: I was mistaken about sudo. I had assumed modem-manager was not running. From comment #14 in Bug #410634: 
> To get the log of modem-manager, you need to kill the previously running process launched at boot time. Otherwise you will get a dbus error.

---

### Post by GeorgeVita on 2009-08-13
> 1) Stop NetworkManager
2) run /usr/sbin/modem-manager --debug
3) Start NetworkManager
4) Plug in your modemIn 'plain' command line is:```
g@KKa4:~$ sudo /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                    [ OK ]
g@KKa4:~$ ps -A | grep modem
 2292 ?        00:00:00 modem-manager
g@KKa4:~$ sudo kill 2292
g@KKa4:~$ sudo /usr/sbin/modem-manager --debug
** Message: Loaded plugin Huawei
** Message: Loaded plugin Option High-Speed
...
g@KKa4:~$ sudo /etc/init.d/NetworkManager start
 * Starting network connection manager NetworkManager           [ OK ] 
g@KKa4:~$
```

> **From [https://bugs.launchpad.net/bugs/410634](https://bugs.launchpad.net/bugs/410634)**
I am just adding the detailed procedure I used to get the 'modemmanager log data' (in case a less experienced user like me is trying to find it):

0. boot without the modem, wait for the system to fully load

1. open a terminal window and stop network manager: ```
sudo /etc/init.d/NetworkManager stop
```
system responds: * Stopping network connection manager NetworkManager [ OK ]

2. find the modem-manager process number: ```
ps -A | grep modem
```
system responds: 2292 ? 00:00:00 modem-manager
where in above example '2292' was the process number

3. kill the modem-manager process: ```
sudo kill 2292
```
REPLACE 2292 with your results

4. run modem-manager in debug mode: ```
sudo /usr/sbin/modem-manager --debug
```
system responds some messages and remain there waiting for new triggers:
** Message: Loaded plugin Huawei
** Message: Loaded plugin Option High-Speed
...

5. open a NEW terminal window to start network manager: ```
sudo /etc/init.d/NetworkManager start
```
system responds: * Starting network connection manager NetworkManager [ OK ]

6. attach modem, wait at least 30 seconds for the full initialization

7. try to connect via network manager icon

8. wait at least 1 minute for the connection and if not established clisk disconnect

9. disconnect modem

Finally copy paste all data from first terminal window (containing log data).

Regards,
George

P.S. I believe that my E169 problem is similar to E220 and I am not going to open a new 'bug' report


And also copy comment #25 of [https://bugs.launchpad.net/bugs/410634](https://bugs.launchpad.net/bugs/410634) > **Also, I'd like to request that if you're having NM 0.8 3G problems and you *don't have an Huawei E220*, please open a new bug, as these problems are usually vendor specific. Thanks!**


Regards,
George

---

### Post by Sycron on 2009-08-14
i installed today the alpha 4 on eeepc and i can't connect with e220. When i try to get online it stays forever as "acquiring new address" and never connects.

are there any workarounds? i'm using NM0.7.995

---

### Post by tekstr1der on 2009-08-14
The workaround is to downgrade to network-manager 0.7.1.git.5.272c6a626-0ubuntu1 and purge modemmanager. This will restore functionality. Before you do that though, you could post some debug info on the bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/410634](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/410634)

> Modems are handled by ModemManager now, which is more flexible and a better architecture for the future. To help us figure out what's going on now, please follow these steps:

1) Stop NetworkManager
2) run /usr/sbin/modem-manager --debug
3) Start NetworkManager
4) Plug in your modem

And tell us what log output ModemManager spews out.

---

### Post by Sycron on 2009-08-14
Done with the logs! Can I connect bluetooth DUN in karmic? I tried with blueman but doesn 't work, damn regression.

---

### Post by GeorgeVita on 2009-08-15
... and as we are waiting for the 'bug to be solved', below is how I connected and post this message using only a terminal command:

ubuntu 9.10 Alpha 4 + updates, Huawei E169, WIND GR, 'terminal only connection' ```
g@KKa4:~$ sudo pppd ttyUSB0 460800 nodetach defaultroute noipdefault noauth lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" "OK" "atdt*99***1#" "CONNECT"' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 212.152.81.8
remote IP address 10.64.64.64
primary   DNS address 212.152.70.6
secondary DNS address 212.152.70.7 
```

>>> adding parameter **debug** (sudo pppd ttyUSB0 460800 nodetach **debug** ...) you can see more info about connection

Regards,
George

P.S. thanks to [DustStuff]("http://ubuntuforums.org/showthread.php?p=8899463") for corrections.

---

### Post by GeorgeVita on 2009-08-19
Now works for my E169 after placing 'trunk' instead of 'ppa' for network manager updates at Software Sources.

HowTo: **[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)**

Original info from similar problem: [http://ubuntuforums.org/showthread.php?t=1234004](http://ubuntuforums.org/showthread.php?t=1234004)

Regards,
George

---

### Post by tekstr1der on 2009-08-19
Confirmed fixed for the Verizon UM150 (bug #410386) reported in the OP also.

This appears to be fixed with latest build:
network-manager - 0.8~a~git.20090817t203502.3e22183-0ubuntu1~nmt2
modemmanager - 0.2.git.20090817t181641.ca767e4-0ubuntu1~nmt2

Found here:
[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

CDMA modem is connecting as expected with the only difference from .7.1 being that instead of "auto mobile broadband", now user must select provider from list to set up connection.

---

### Post by andresmh on 2009-08-19
I think this is the same bug I submitted for my CDMA modem (verizon):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405053)

---

### Post by Amaranth on 2009-08-20
Looks like using the daily builds from the NetworkManager PPA may fix this. Can someone try it out?

---

### Post by plun on 2009-08-20
> **Amaranth said:**
> Looks like using the daily builds from the NetworkManager PPA may fix this. Can someone try it out?

Yup, works just fine.

"asac" about the test ppa:
[http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html](http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html)

ppa adress:
[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

hardware:
Option Globetrotter GIO225, Telenor Sweden


--

---

### Post by GeorgeVita on 2009-08-20
> **Amaranth said:**
> Looks like using the daily builds from the NetworkManager PPA may fix this. Can someone try it out?

Already test it and works with '**trunk**' version. Trunk site of N.M states: 'Daily builds coming soon'.

> **GeorgeVita said:**
> Now **works** for my E169 after placing 'trunk' instead of 'ppa' for network manager updates at Software Sources.
HowTo: **[https://edge.launchpad.net/~network-manager/+archive/[B]trunk**](https://edge.launchpad.net/~network-manager/+archive/[B]trunk**)[/B]> **tekstr1der said:**
> Confirmed fixed for the Verizon UM150 (bug #410386) reported in the OP also.
This appears to be fixed with latest build:
network-manager - 0.8~a~git.20090817t203502.3e22183-0ubuntu1~nmt2
modemmanager - 0.2.git.20090817t181641.ca767e4-0ubuntu1~nmt2
Found here: [https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)> **plun said:**
> Yup, works just fine.
ppa adress:[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)
hardware:Option Globetrotter GIO225, Telenor Sweden

BUT from following your post I check again the default PPA coming with the standard karmic upgrades and DID NOT work! As it works with the 'trunk' version I believe this is '**solved**' now and it is just a matter of time to come with the normal karmic daily build.

-------

> **andresmh said:**
> I think this is the same bug I submitted for my CDMA modem (verizon):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405053)

Hi **andresmh**, your problem is slight different as it happens after suspend. It is possible to be solved with the new version as it uses newer methods (modem manager) so you must check it. Some other ideas already posted to your thread: [http://ubuntuforums.org/showthread.php?t=1222870](http://ubuntuforums.org/showthread.php?t=1222870)
 
-------

Regards,
George

---

### Post by plun on 2009-08-20
> **GeorgeVita said:**
> 
BUT from following your post I check again the default PPA coming with the standard karmic upgrades and DID NOT work! As it works with the 'trunk' version I believe this is '**solved**' now and it is just a matter of time to come with the normal karmic daily build.



The trunk works just fine for me and was updated 5 hours ago (look at the files).

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

With standard Karmic it doesnt work and I must switch to my Jaunty partition for using my modem.

---

### Post by tekstr1der on 2009-08-20
> **Amaranth said:**
> Looks like using the daily builds from the NetworkManager PPA may fix this. Can someone try it out?

Yeah.. this was discussed, confirmed and linked yesterday two and three posts above yours.

Wanted to add that there is an issue still with reconnecting during the same session. 

> Rob Adams  wrote:

OK what happens now is that it works the first time, but if I plug it in, connect, then disconnect and unplug it, I can no longer ever get it working again until I reboot.


> tekstr1der  wrote:

I can confirm the reconnect problem. To workaround, I killed modem-manager and restarted networking. This allows the device to connect again without the need to log out.

Should the failure to reconnect be filed as a separate bug?


```
sudo killall modem-manager
sudo /etc/init.d/networking restart
[Alt-F2]modem-manager
```

---

### Post by tekstr1der on 2009-08-20
Also the reconnect issue is still present with latest builds:

```
network-manager - 0.8~a~git.20090818t172856.a8ca7f5-0ubuntu1~nmt2
modemmanager - 0.2.git.20090819t220813.1a75d8d-0ubuntu1~nmt1
network-manager-applet - 0.8~a~git.20090818t151413.a8b7eed-0ubuntu1~nmt3
```

---

### Post by erkiha on 2009-08-20
This PPA cured my network-manager and huawei 3g modem:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main

---

### Post by GeorgeVita on 2009-08-20
> **tekstr1der said:**
> Also the reconnect issue is still present with latest builds:```
network-manager - 0.8~a~git.20090818t172856.a8ca7f5-0ubuntu1~nmt2
modemmanager - 0.2.git.20090819t220813.1a75d8d-0ubuntu1~nmt1
network-manager-applet - 0.8~a~git.20090818t151413.a8b7eed-0ubuntu1~nmt3
```

For me (Huawei E169 on EeePC 1000H above versions) running:```
g@KKa4:~$ uname -a
Linux KKa4 2.6.31-999-generic #200908191246 SMP Wed Aug 19 12:36:49 UTC 2009 i686 GNU/Linux
```
**Works OK!**
My actions: boot without modem, **wait** for the system to load and then:
attach modem, **wait** some seconds, check if mobile connection exists at nm-icon, connect, firefox browsing, disconnect, **wait** 5 seconds, remove modem, **wait** 5 seconds and all again from 'attach modem'

Note the small waits (5 seconds minimum) for the system to settle drivers/ports. I also check by changing USB ports, resulting OK again. I noticed a small delay but this must be the time needed to find the 3G network.

@**tekstr1der**
Check with the later kernel (?) and check if /dev/ttyUSBx ports are there... If you can repeat it with your modem must be a 'bug', so report it.

Regards,
George

---

### Post by tekstr1der on 2009-08-20
GeorgeVita - Perhaps you are misunderstanding me. The original issue of connection IS confirmed fixed with the latest PPA trunk build.

There is a new issue with being able to reconnect. This is noted in the bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/410386)

STR:

1) Plug in USB Modem Device
2) Establish connection through network manager applet
3) Disconnect through network manager applet
4) Remove device from port
5) Plug in USB Modem Device

Result:

Cannot re-establish connection. Need to follow steps in previous post.

EDIT: Once the new network-manager packages land on karmic updates, I will be filing a new bug for this issue per Tony Espy

---

### Post by GeorgeVita on 2009-08-20
Hi **tekstr1der**, I fully understood and tried to simulate your NEW problem. With my h/w (E169, EeePC 1000H) it is not happened. I realized just a small delay (gray cirles spinning for 2-5 seconds) when reconnecting after the physical removal/attachment. I tested 4 times (connection, disconnection, removal, attachment, connection again) using the same or other USB port. I believe that the new problem is more h/w (modem?) specific.

The idea is to check what is happening to the /dev/ttyUSBx ports (no creation or hold/locked by modem manager). When testing the initial problem I couldn't connect via other methods (pppd, wvdial) unless the modem was unplugged or modemmanager was 'killed'. Some times to 'kill' modem manager I had also to stop network manager.

Regards,
George

P.S. I can do any test if you need for comparison.

---

### Post by tekstr1der on 2009-08-20
GeorgeVita- Thanks for making that clear. Looks like this issue may be specific to Verizon (Pantech) hardware.

Each successive time I kill modem-manager then insert the device it does indeed create a new /dev/ttyACMx with x incrementing by one each time.

---

### Post by GeorgeVita on 2009-08-20
Hi **tekstr1der**,
I managed to make the shift of /dev/ttyUSBx ports!
Using 'typical' 2.6.31-6-generic #25-Ubuntu kernel I connected and then  close the lid of my netbook. Suspend/resume did the rest...```
...
[  482.676190] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  482.832475] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[  482.832483] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[  482.832655] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[  482.848760] ata1.00: configured for UDMA/100
[  482.864757] ata1.00: configured for UDMA/100
[  482.864771] ata1: EH complete
[  483.430360] sd 0:0:0:0: [sda] Starting disk
[  483.544090] usb 1-8: reset high speed USB device using ehci_hcd and address 4
[  483.840102] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[  483.990608] option 2-2:1.0: no reset_resume for driver option?
[  483.990619] option 2-2:1.1: no reset_resume for driver option?
[  483.990629] option 2-2:1.2: no reset_resume for driver option?
[  483.990936] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  483.990966] option 2-2:1.0: device disconnected
[  483.991087] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  483.991124] option 2-2:1.1: device disconnected
[  483.991237] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  483.991271] option 2-2:1.2: device disconnected
[  484.100077] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  484.823484] btusb 5-1:1.0: no reset_resume for driver btusb?
[  484.823496] btusb 5-1:1.1: no reset_resume for driver btusb?
[  485.072789] option 2-2:1.0: GSM modem (1-port) converter detected
[  485.072938] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  485.073170] option 2-2:1.1: GSM modem (1-port) converter detected
[  485.073285] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  485.073446] option 2-2:1.2: GSM modem (1-port) converter detected
[  485.073556] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
[  485.073769] PM: resume devices took 3.880 seconds
[  485.073837] PM: Finishing wakeup.
[  485.073841] Restarting tasks ... done.
```

But my modem is Huawei and can connect from /dev/ttyUSB0 or /dev/ttyUSB1 (I checked that the 1st was ttyUSB0 and after resume ttyUSB1).
Next resume created ttyUSB0-2-3, other created 123, 023, 012 etc. always connected from 0 or 1

>>> ttyUSB0-1-2 are coming back with: nm stop, kill mm, -r option, option, nm start
>>> **modem-manager runs always if network manager is running** (kill just restart it)
>>> **to kill modem-manager you must first stop network manager!**```
g@KKa4:~$ ps -A | grep modem
 5493 ?        00:00:00 modem-manager
g@KKa4:~$ sudo killall modem-manager
g@KKa4:~$ ps -A | grep modem
 5504 ?        00:00:00 modem-manager
g@KKa4:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                       [ OK ] 
g@KKa4:~$ ps -A | grep modem
 5504 ?        00:00:00 modem-manager
g@KKa4:~$ ls /dev/ttyU*
/dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3
g@KKa4:~$ sudo /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                        [ OK ] 
g@KKa4:~$ sudo killall modem-manager
g@KKa4:~$ ps -A | grep modem
g@KKa4:~$ ls /dev/ttyU*
/dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3
g@KKa4:~$ sudo modprobe -r option
g@KKa4:~$ sudo modprobe option
g@KKa4:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
g@KKa4:~$ sudo /etc/init.d/NetworkManager start
 * Starting network connection manager NetworkManager                        [ OK ] 
g@KKa4:~$ ps -A | grep modem
 5605 ?        00:00:00 modem-manager
``` 
Can you check what happens to the /dev/ttyACMx? Next time you are going to post to launchpad, state clearly that your modem uses ttyACM0 (it possibly uses more drivers).

Regards,
George

---

### Post by tekstr1der on 2009-08-21
Since the new builds landed in updates, I filed:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913)

Regarding the failure to reconnect.

---

### Post by linux6994 on 2009-08-21
This bug caused me to have to drop back to Jaunty since I run totally wireless either broadband or wifi :( when its fixed I will be back up on Karmic. Alphas are fun.

---

### Post by GeorgeVita on 2009-08-21
Hi **linux6994**,
why not trying other 'bullet proof' methods that work from terminal and can connect you all times? I mean wvdial, pppconfig or just pppd (or even downgrade N.M. for a while?)

The alphas will be back again!

I returned to wvdial when a bug (on alpha 2) broke graphic environment. I am using only 3G for internet connection and NM could not run.

Regards,
George

---

### Post by fluffman86 on 2009-08-24
I couldn't get pppconfig or wvdial to work, and the current trunk is still broken with my E71x.  Dropping to 0.7.1 works great, though.

[https://bugs.launchpad.net/bugs/418368](https://bugs.launchpad.net/bugs/418368)

---

### Post by tekstr1der on 2009-09-14
Wow. Finally, after recent updates to network-manager and modemmanager, I can connect my USB 3G device and it just works like it used to. No need to kill off modemmanger first to connect.

Also, subsequent connections during the same user session, after the device has been removed, work as well. Updating my bug report ( [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/416913) ) to reflect this.

---

