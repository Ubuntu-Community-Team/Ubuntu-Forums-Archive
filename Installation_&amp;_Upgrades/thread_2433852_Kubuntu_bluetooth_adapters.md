---
title: "Kubuntu bluetooth adapters"
date: 2019-12-26
forum: Installation &amp; Upgrades
---

### Post by abuti-jj on 2019-12-26
KUBUNTU BLUETOOTH ADAPTERS


Hi,

I'm not good at linux, but somehow I managed to make wifi work after  following some website advice. Could you help me with bluetooth adapter.
So far I have done the following:


sudo apt-get install dkms git build-essential
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf

after the last line, it shows: echo "options rtl8723de ant_sel=2" 

What should I do next to make bluetooth adapters found?

My system information:

                       system         Computer
/0                     bus            Motherboard
/0/0                   memory         8GiB System memory
/0/1                   processor      Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
/0/100                 bridge         Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
/0/100/2               display        HD Graphics 620
/0/100/4               generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
/0/100/8               generic        Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
/0/100/14              bus            Sunrise Point-LP USB 3.0 xHCI Controller
/0/100/14.2            generic        Sunrise Point-LP Thermal subsystem
/0/100/16              communication  Sunrise Point-LP CSME HECI #1
/0/100/17              storage        Sunrise Point-LP SATA Controller [AHCI mode]
/0/100/1c              bridge         Sunrise Point-LP PCI Express Root Port #5
/0/100/1c/0    eno1    network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.5            bridge         Sunrise Point-LP PCI Express Root Port #6
/0/100/1c.5/0  wlo1    network        RTL8723DE 802.11b/g/n PCIe Adapter
/0/100/1f              bridge         Sunrise Point LPC Controller/eSPI Controller
/0/100/1f.2            memory         Memory controller

uname -r

5.3.0-24-generic

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b5db Chicony Electronics Co., Ltd HP Webcam
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks

---

