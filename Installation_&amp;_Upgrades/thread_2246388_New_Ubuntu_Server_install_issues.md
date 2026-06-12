---
title: "New Ubuntu Server install issues"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by Hugo_Drolet on 2014-09-30
Hey Ubuntu forums, 

I recently bought a used Supermicro server and I am trying to have it running at home but I am having issues with the os (ubuntu server) setup.

It is mainly going to be used as a file server (samba) and media streaming box (PS3mediaserver). And I'd like to run a web/ftp server at some point to host my personnal website.


Here are the box's specs:

CPU: Dual Intel Xeon 5335e 
RAM: 16Gb 333mhz  (16x1)
MB: Supermicro X7DBE+
Raid card: 3ware 9650se-8lpml
OS HDD: 1Tb seagate certified repair 
PSU: 850W (redundant)
I am using a PS2 keyboard.

At first I had installed LinuxMint with KDE to check if the machine worked properly. And it did. I then decided to install Ubuntu Server 14.04.1. First issue showed up during the install process, Ubuntu Server didn't find the network adapter, I got "No networks interfaces detected". I continued the install process anyway. Everithing was installed on the 1TB hdd listed above. I used "Guided - Use entire disk and setup LVM" and installed GRUB. 

The second issue I encountered was the boot hanging at "Adding swap" line. Simillar to this: 
[http://serverfault.com/questions/546079/ubuntu-server-hanging-on-adding-swap](http://serverfault.com/questions/546079/ubuntu-server-hanging-on-adding-swap)
I tried the fixes suggested on this forum, nothing worked.

I then tried to install 10.04 LTS instead. It still did pickup the network adapter. But this time at boot it just showed a blinking white ticker and I couldn't type anything.

Any help is appreciated. Let me know if you need more info!

Thanks in advance for your help!

---

### Post by Michael_McKenney on 2014-09-30
Do you have an adequate circuit to run the dual 850W power supplies?  The Supermicro servers need a decent circuit and can run noisy with its cooling fans kicking fully on.  They also are designed for enterprise Linux so they may not be easy to get to work with Ubuntu.  I would try 14.04 Live CD to test with.  I was able to get 14.04 to work on my Tyan Thunder K8WE Server board. It found all the hardware onboard and in the PCIe and PCI-X slots.  Today, I am replacing the NIC adapter with a Intel NIC from Micro Center.  The Nvidia pro 2200 and 2050 stuff does not work well in Ubuntu.  Performance is poor on the drivers.

---

### Post by Hugo_Drolet on 2014-09-30
The server is plugged into a wall outlet and is pretty much alone on the circuit. And I as stated in the original post, the box worked fine with LinuxMint. And I think there are no LiveCd for the server version of Ubuntu. And since the box will be running headless there is no use for the desktop version. 

What would you suggest me to do, get a new NIC? And the current network adapter is by intel (82563EB) not nvidia.
[http://www.supermicro.com/products/motherboard/Xeon1333/5000P/X7DBE.cfm](http://www.supermicro.com/products/motherboard/Xeon1333/5000P/X7DBE.cfm)

Thanks!

---

### Post by Michael_McKenney on 2014-09-30
It might be an option.  I found one that works at Micro Center for $40 and has good performance.  Not worth wasting hours trying to get the onboard drivers to perform better against spending $40.  It could be the chipset drivers are not loading that is causing the NIC not to be found.  What does lspci show?

---

### Post by Hugo_Drolet on 2014-09-30
I can't really check lspci since I cannot get Ubuntu to boot at all... Wouldn't it be better for me to fix the booting issue before looking into the adapter?

Thanks for your reply!

---

### Post by Michael_McKenney on 2014-09-30
Did you allow swap space for 16-24GB?  Linux usually wants a swap file 1-1.5x your RAM.   Try reducing the RAM to 4GB and see if the install works?

---

### Post by Hugo_Drolet on 2014-09-30
I installed 14.04 using the "guided install, use all disk" Would you suggest I reinstall 14.04 using manual partitionning and allocate 24Gb to a swap partition?

---

### Post by Michael_McKenney on 2014-09-30
I have not played with Ubuntu on a box with over 4 GB lately.   It might be worth trying.  You want a swap partition for system error dumps.  Post the exact error?   I know that best practice is not to install /tmp or /swap in RAID 5.  They should be on JBOD (single disk) or RAID 1.  RAID 5 can cause slow downs due to parity writes.

---

### Post by Hugo_Drolet on 2014-09-30
Thanks for your answer I'll try that tonight and post the results back here!

---

