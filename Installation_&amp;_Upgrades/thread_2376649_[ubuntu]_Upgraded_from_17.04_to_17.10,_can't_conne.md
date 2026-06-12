---
title: "[ubuntu] Upgraded from 17.04 to 17.10, can't connect to dns &quot;Server not found&quot;"
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by mschet on 2017-11-04
Hi, I've been successfully upgrading every time new releases come out since about 2011 without problem, but this latest upgrade to 17.10 has messed up my internet (DNS) settings somehow.   Like other people have reported, I'm getting an internet connection, but can't connect to websites or run updates etc... either over wired (what I normally connect with) or even wifi connections.

The solutions that appear to have worked for others aren't working for me... The last thing I tried was to turn on dnsmasq ON, by editing /etc/NetworkManager/NetworkManager.conf and adding  [main] dns=dnsmasq

no dice.

Help!  What can I do to get the internet working on my ubuntu system?

Edit: in case it helps someone diagnose, here are the results when I run 'sudo lshw -C network':
 *-network UNCLAIMED       
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0700000-c0707fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: enp14s0
       version: 0c
       serial: 30:f9:ed:a7:55:13
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.11 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:29 ioport:2000(size=256) memory:c0500000-c0500fff memory:c0400000-c0403fff

cat /etc/resolv.conf  returned: 

nameserver 127.0.0.53
search hitronhub.home

---

### Post by ajgreeny on 2017-11-04
Just out of interest in terminal try **ping 216.58.212.142** and then to confirm your DNS failure try **ping google.com** which should both go to the same place but I anticipate the named version failing.

What is shown as your primary DNS server if you view connection info from the network icon in the panel?

---

### Post by mschet on 2017-11-04
The first ping works, pinging google.com results in "name or service not found", and the network icon has changed in 17.10 due since it's GNOME I guess, so when I click on "wired settings" and the config wheel icon, after DNS: it lists "192.168.0.1 8.8.8.8"   The 8.8.8.8 is likely from my trying to fix the issue by following other advice on this forum or on askubuntu.  I have 8.8.8.8 under DNS in the IPv4 tab

---

### Post by ajgreeny on 2017-11-04
Is the 8.8.8.8 shown as your secondary DNS?

---

### Post by mschet on 2017-11-04
No, I think at some point I put 8.8.4.4 as my secondary DNS somewhere, as per some other thread about the same issue, but here it reads this, since I have 8.8.8.8 under DNS in the IPv4 tab.   I can clear that, it makes no difference, 'server not found' either way.

---

### Post by ynota on 2017-11-05
you could check your "/etc/resolv.conf" file with > cat /etc/resolv.conf This will show if a name server has been added by networkmanager. if there is not any there you can manually add the google dns server with > sudo echo "nameserver 8.8.8.8" >> /etc/resolvconf/resolv.conf.d/tail and then restart your resolved.service with > sudo systemctl restart systemd-resolved.service that should get dns working again for you

---

### Post by mschet on 2017-11-05
> **ynota said:**
> you could check your "/etc/resolv.conf" file with  This will show if a name server has been added by networkmanager. if there is not any there you can manually add the google dns server with  and then restart your resolved.service with  that should get dns working again for you

Thanks ynota - the cat /etc/resolv.conf  returned: 

nameserver 127.0.0.53
search hitronhub.home

I tried adding the google server anyway, but when I  run  'sudo echo "nameserver 8.8.8.8" >> /etc/resolvconf/resolv.conf.d/tail', I get a permission denied error.

EDIT: when I dual boot into windows, my connection info is as follows: 
IPv6 address:    fd00:fc:8dfe:e902:c15e:c67d:5366:2c3a
IPv4 address:    192.168.0.11
IPv4 DNS Servers:    192.168.0.1
Manufacturer:    Realtek
Description:    Realtek PCIe GBE Family Controller
Driver version:    8.10.1226.2012
Physical address:    &#8206;30-F9-ED-A7-55-13

---

### Post by ynota on 2017-11-07
mschet I assumed you had sudo set up on your system and were able to use the sudo command to edit system files. Are you able to log in as root (or su into root from your login) so you can edit the [COLOR=#000000]/etc/resolvconf/resolv.conf.d/tail[/COLOR] file? You could also edit the /etc/resolv.conf file directly, this will give you a temporary fix until network manager overwrites it. Changing the [COLOR=#000000]/etc/resolvconf/resolv.conf.d/tail[/COLOR]  file is a better long term option as it will keep adding your nameserver entry to the end of the /etc/resolv.conf file on each reboot.

---

### Post by mschet on 2017-11-07
I do have a sudo setup, and I get a permission denied error. I am not able to login as su or root.

running 'ls -l /etc/resolvconf/resolv.conf.d/' 
returns:

-rw-r--r-- 1 root root   0 Jun  3  2015 base
-rw-r--r-- 1 root root 282 Nov 28  2016 head
lrwxrwxrwx 1 root root  37 Nov  5 06:16 original -> /run/systemd/resolve/stub-resolv.conf
--w------- 1 root root   0 Nov  4 08:26 tail

and

$ sudo echo "nameserver 8.8.8.8" >> /etc/resolvconf/resolv.conf.d/tail
yields:
bash: /etc/resolvconf/resolv.conf.d/tail: Permission denied

---

### Post by ynota on 2017-11-11
Sorry mychet, I just found that I gave you bad advice. You can't use echo to append "nameserver 8.8.8.8" to that file.. (that will teach me to try it first before posting). 
You will be able to use a file editor (such as vi or nano) with the sudo command to edit the file (I have tested this :D)
> sudo vi /etc/resolvconf/resolv.conf.d/tail then add the "nameserver 8.8.8.8" line and save the file, following that you[COLOR=#000000] restart your resolved.service as i mentioned earlier and your dns request will see the new server address.[/COLOR]

---

### Post by mschet on 2017-11-11
did it, but still can't ping google.com... I'm just about to throw in the towel, install 16.04lts instead, and hope whatever the hell problem this is, is ironed out by 18.04.  It's a sony laptop, not some weird setup... I'm guessing it might be the broadcom driver issue coming up again.  Anyway, thanks for trying, unless you can think of anything else to try, I'm just about to try to install 16.04 without losing my data (backed up anyway).

---

### Post by nrg753 on 2017-11-18
I just had weird dns problems on 17.10 where I couldn't connect at all. In my case I didn't have resolvconf installed and the resolve.conf file was being controlled by the dnsmasq plugin of network manager.

What worked for me was editing **/etc/NetworkManager/NetworkManager.conf** eg:
```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

Then add **dns=dnsmasq** under **[main]**, my file now looks like
> 
[main]
plugins=ifupdown,keyfile
**dns=dnsmasq**

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no


Now restart NetworkManager with:
```

sudo systemctl restart NetworkManager

```

Hopefully this helps someone out!

---

