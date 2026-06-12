---
title: "Installed VMWare, lost wireless"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2007-06-20
I successfully installed vmware, but somehow it disabled my wireless. I have the dreaded Broadcom chipset for my Dell WLAN 1390. I tried a bunch of things to get the card to work, but to no avail. I tried ndiswrapper, bcmfcutter, and using the one provided in Ubuntu ( which is the one that worked previously.

I probably jacked up some config files somewhere. Could someone help me out on trying to figure out what went wrong and how to fix this?
I don't know what files to look in.

---

### Post by lsutiger on 2007-06-20
bump

---

### Post by lsutiger on 2007-06-20
Ok I reinstalled Ubunty Feisty, followed the instructions to a 'T' for getting wireless working, and still nothing. It seems I burned up my wireless card.
Can someone, or some guru help me out here before I go buy a new one?

---

### Post by itsdaveperdue on 2007-06-22
Did you reinstall VMWare?

I have a Broadcom 4309 chipset using the bcm43xx drivers.  I'm troubleshooting a problem I have with my wireless not connecting to unencrypted networks, and it seems that if I startup a virtual machine and connect the wifi bridged network that my (K)ubuntu side starts working...weird.

I stopped the VMWare services (sudo /etc/init.d/vmware stop), but the problem remains.  I'm going to remove VMWare bridging and see if that works.

If you're just trying to get your wireless working, enable the extra repositories and install bcm43xx-fwcutter; it should automagically download and install the firmware.

---

### Post by lsutiger on 2007-06-22
Hey Dave!
I did not reinstall VMWare yet. Thank God I know how to backup! I reinstalled, and got my wireless working ( though only @ 11Mbs ). I plan on buying the famous to work OOB [Intel wireless card mentioned here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106001") for my laptop. 
Tell me how your experiment goes :D

PS - What version of Ubuntu are you running?

---

