---
title: "network problem"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Totzo on 2009-08-04
Anyone else having network conection problems this morning? Tried doing "/etc/init.d/networking restart" and no joy- works fine in other os so it's definately karmic related.

---

### Post by infamousrev on 2009-08-04
Im having network problems also

Asus eeepc 1000HE :

 *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:43:71:51:93
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.0.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:fbef0000-fbefffff


The network problem makes the wireless fail to connect.

The program causing the problem appears to be apparmor

> 
sudo apt-get remove apparmor apparmor-utils 


The above command fixed this problem.

**Beware however, apparmor is a security program, removing it [color=red]might make your machine more vulnerable.[/color]**

---

### Post by jithin1987 on 2009-08-04
Same issue here. Started after an update for apparmor packages. 

stopping apparmor and restarting Networkmanager fixed the issue.

sudo /etc/init.d/apparmor stop
sudo /etc/init.d/NetworkManager restart

Wondering why an apparmr update breaks the entire networking.

---

### Post by taavikko on 2009-08-04
> **infamousrev said:**
> 
The program causing the problem appears to be apparmor



The above command fixed this problem.

**Beware however, apparmor is a security program, removing it [color=red]might make your machine more vulnerable.[/color]**

Ah, somebody already replied, but yes,
```
sudo service apparmor stop
```
is enough for the session to get the wireless back online.

---

### Post by Totzo on 2009-08-04
that fixed it for me too, thanks :D

---

### Post by Leighman on 2009-08-04
Had the same problem here.
Will have to give the solution a go =D

---

### Post by tekstr1der on 2009-08-04
I have the same symptoms. Filed:
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/408829](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/408829)

---

### Post by mdeslaur on 2009-08-04
Updated apparmor packages (2.3.1+1403-0ubuntu9) to fix this known issue were pushed to the archive and should be available soon.

Please do not uninstall apparmor, just stop the service temporarily. Removing apparmor will reduce the security measures in place to prevent compromise in case of a security vulnerability.

We apologise for this regression.

---

### Post by Slug71 on 2009-08-04
And here i thought it had something to do with the NM updates that came through.

---

### Post by Sub101 on 2009-08-04
Just to add, am having the same issue. I will try the fix.

EDIT: Completed the above fix which worked, and the new updates fixed the problem.

---

### Post by lonniehenry on 2009-08-04
Updated apparmor packages (2.3.1+1403-0ubuntu9) are out and fixed the problem.  Do the updates.

---

### Post by xebian on 2009-08-04
> **lonniehenry said:**
> Updated apparmor packages (2.3.1+1403-0ubuntu9) are out and fixed the problem.  Do the updates.

No cigar.  Have to purge apparmor completely to get it working.

Other users may have issues here.  How can they get the update when there is no network?  It's like the "..NO KEYBOARD DETECTED..PRESS ANY KEY TO CONTINUE.. " thing.

---

### Post by tekstr1der on 2009-08-04
> **jithin1987 said:**
> 

sudo /etc/init.d/apparmor stop
sudo /etc/init.d/NetworkManager restart



Simply stop apparmor and restart your networking. Then you will be able to download and install the updated apparmor packages. Problem solved. No need to purge.

---

### Post by phenest on 2009-08-05
Todays updates have fixed this.

---

### Post by amauk on 2009-08-06
Updates to apparmor didn't automatically fix the problem for me, for some reason

Had to do
```
sudo dpkg-reconfigure apparmor
```

and after a reboot, all is well

Just in case others were still having networking issues

---

### Post by zenarcher on 2009-08-07
> **amauk said:**
> Updates to apparmor didn't automatically fix the problem for me, for some reason

Had to do
```
sudo dpkg-reconfigure apparmor
```

and after a reboot, all is well

Just in case others were still having networking issues

I have just done a fresh install of Kubuntu 9.10, downloading the daily build.  My wireless was working fine until I did all the available updates, including the apparmor updates.  As soon as I completed all current updates and rebooted, I cannot connect with my wireless.  I can configure the wireless just fine...sees my linksys router and all.  I can see the connection up and running from the connection icon on the taskbar at the bottom of the screen, but cannot get a connection...cannot open Firefox or anything that requires online access.  I can connect an ethernet cable and connect just fine...but not with my wireless using an Atheros chipset which works fine with everything but the latest 9.10 update.

I have tried running sudo /etc/init.d/appormor stop and sudo /etc/init.d/NetworkManager restart as well as sudo dpkg-reconfigure apparmor without any success.

Does anyone have anything else I can try or figured out a way to get the wireless working again?  If I need to post some troubleshooting, please advise what to run to provide the information.

It appears that the wireless connection is up and working, but that everything is blocked for access.  Maybe that will help.

Thanks,
zenarcher

---

### Post by zenarcher on 2009-08-07
If it's any help, here's what I get when I run nm-tool from a terminal with my ethernet connection disconnected and just my wireless active:

zenarcher@zenarcher-desktop:~$ nm-tool

NetworkManager Tool

State: disconnected


** (process:3553): WARNING **: <WARN>  get_one_connection(): error: invalid connection: 'NMSettingConnection' / 'uuid' invalid: 1                               


** (process:3553): WARNING **: <WARN>  get_one_connection(): error: invalid connection: 'NMSettingConnection' / 'uuid' invalid: 1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:11:F5:3E:05:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
    linksys:         Infra, 00:16:B6:CD:FB:05, Freq 2437 MHz, Rate 54 Mb/s, Strength 100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:24:21:1D:B3:26

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by zenarcher on 2009-08-07
Well, if anyone else is experiencing the problem I have, I installed wicd and that fixed it.  I was able to get my wireless working fine that way.

Cheers,
zenarcher

---

### Post by caryb on 2009-08-07
This problem is in Kubuntu as well. I ran nm-tool my wireless is disconnected as well. I tried the apmor fix but for some reason it's not installed on my lappy.


Cary

---

### Post by zenarcher on 2009-08-07
Yes, my problem was with Kubuntu, as well.  I tried the same things you tried with no success.  I was happy that wicd resolved the problem for me.

Cheers,
zenarcher

---

### Post by caryb on 2009-08-07
I would like to resolve this without wicd as I have quiet a lot of users who will be upgrading to karmic & it would be good for this to be going by then.


Cary

---

### Post by zenarcher on 2009-08-07
I can understand that feeling.  I hope they get this resolved before long.

Cheers,
zenarcher

---

### Post by taavikko on 2009-08-08
> **zenarcher said:**
> Yes, my problem was with Kubuntu, as well.  I tried the same things you tried with no success.  I was happy that wicd resolved the problem for me.

Cheers,
zenarcher

[https://bugs.edge.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593](https://bugs.edge.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593)

---

### Post by slakkie on 2009-08-08
I have a similar problem.

I use ifplugd/guessnet/wpa_supplicant to connect to my networks, I noticed the network managers were started but /etc/init.d/networking wasn't..

---

