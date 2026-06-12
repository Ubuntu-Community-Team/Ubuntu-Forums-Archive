---
title: "USBs not working on Ubuntu 10.04"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by Mortesins93 on 2010-08-24
Hello,
I used to have an Ubuntu 8.10 which worked just fine but after some internet problems (which I could have probably solved with ndiswrapper) I freshly installed Ubuntu 10.04. The internet problems was still there and I solved it (for now) with ndiswrapper. Now my problem is that the internet randomly disconnects sometimes and this is the output of dmesg | tail when it happens:
jessica@jessica-desktop:~$ dmesg | tail
[  246.772159] hub 1-0:1.0: unable to enumerate USB device on port 2
[  247.012036] usb 1-2: new high speed USB device using ehci_hcd and address 9
[  262.104175] hub 1-0:1.0: unable to enumerate USB device on port 2
[  262.344059] usb 1-2: new high speed USB device using ehci_hcd and address 10
[  277.436129] hub 1-0:1.0: unable to enumerate USB device on port 2
[  277.676068] usb 1-2: new high speed USB device using ehci_hcd and address 11
[  292.768145] hub 1-0:1.0: unable to enumerate USB device on port 2
[  293.011357] usb 1-2: new high speed USB device using ehci_hcd and address 12
[  308.100182] hub 1-0:1.0: unable to enumerate USB device on port 2
[  308.340055] usb 1-2: new high speed USB device using ehci_hcd and address 13
jessica@jessica-desktop:~$       
It seems like an USB problem. In fact, besides this internet problem I have problems recognizing usb drives and mounting them. When I plug in a USB drive it doesn't come up on "sudo fdisk -l" so I guess the computer doesn't see it. I already tried usbmount but it doesn't work out for me that well because it mounts my USBs in root and I can't access the files. I had the same USB problem time ago when I unistalled my Xubuntu 9.10 and freshly installed the 10.04 version (still Xubuntu). Coincidence? I don't know.
Anyways, do you know how to solve this problem? If no I'll just downgrade to 9.04 or something. 
Thanks in advance

---

### Post by cypeng on 2010-08-24
Hello,

since you mentioned ndiswrapper, I thought I'd bring your attention to a similar situation I had last night with USB devices not being able to be mounted.  The problem *might* have  something to do with it being loaded before other USB devices.  Or, it  might have something to do with the device driver that ndiswrapper  loaded into memory.  I mentioned this in my post, and showed a kludgy workaround,  here, hoping others may look into it further as well:

[http://ubuntuforums.org/showthread.php?t=1559857](http://ubuntuforums.org/showthread.php?t=1559857)

Good luck!   :smile:

---

### Post by Mortesins93 on 2010-08-25
Ok, so that could be the problem but it is only an Ubuntu 10.04 problem because I have ndiswrapper loaded on my Xubuntu 9.10 and everything seems to be working fine. I guess I'll try unloading the module before plugging in a new USB device and see if it works. So I guess that if no one has a solution, the best fix is going back to Ubuntu 9.10.

---

### Post by Mortesins93 on 2010-08-28
No, I don't think it is ndiswrapper because Ubuntu 10.04 randomly does not see my D-link DWL-G122.
It has to be a problem with the 10.04 because ndiswrapper works fine on my Xubuntu 9.10. Shouldn't the 10.04 be the easiest version??

---

### Post by Mortesins93 on 2010-08-31
Anyone?

---

### Post by Magic_Spehar on 2010-10-12
Hi Mortesen83,

Try the following solution (already posted here by Tarzan)

1. Download Linux driver for RT3070USB from [http://www.ralinktech.com/](http://www.ralinktech.com/) (Software -> Linux)

2. Unpack the tar & bz2 source package, be careful to don't leave spaces in the extracted directory name, open a terminal and go to contents' directory

3.
Code:
cp RT2870STACard.dat RT3070STACard.dat
cp RT2870STA.dat RT3070STA.dat
cp common/rt2870.bin common/rt3070.bin
sudo make
sudo make install
4. Add to /etc/modprobe.d/blacklist.conf
Code:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
5. Make a new dir and copy a RT2870 file in it:
Code:
sudo mkdir /etc/Wireless/RT2870STA
sudo cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
6. Add RT3070STA in /etc/modules

7. Restart the system


__________________

---

### Post by Mortesins93 on 2010-10-13
Thanks a lot, I'll try that.

---

