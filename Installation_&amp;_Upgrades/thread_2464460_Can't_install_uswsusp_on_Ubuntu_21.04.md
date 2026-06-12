---
title: "Can't install uswsusp on Ubuntu 21.04"
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by ayzx2 on 2021-07-02
I am following the post [https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file/1132154#1132154](https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file/1132154#1132154) to enable hibernation on my laptop. While installing uswsusp I am getting 
```

E: Package 'uswsusp' has no installation candidate 

```

Some details about the laptop
```

ayaz@ayaz-HP-Laptop-15s-du3xxx:~/suspend-utils$ lspci 
0000:00:00.0 Host bridge: Intel Corporation Device 9a04 (rev 01) 
0000:00:02.0 VGA compatible controller: Intel Corporation Device 9a78 (rev 01) 
0000:00:04.0 Signal processing controller: Intel Corporation Device 9a03 (rev 01) 
0000:00:08.0 System peripheral: Intel Corporation Device 9a11 (rev 01) 
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller 
0000:00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 20) 
0000:00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 20) 
0000:00:15.0 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 20) 
0000:00:15.1 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #1 (rev 20) 
0000:00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 20) 
0000:00:17.0 System peripheral: Intel Corporation Device 09ab 
0000:00:1d.0 PCI bridge: Intel Corporation Tiger Lake-LP PCI Express Root Port #9 (rev 20) 
0000:00:1d.1 PCI bridge: Intel Corporation Device a0b1 (rev 20) 
0000:00:1e.0 Communication controller: Intel Corporation Tiger Lake-LP Serial IO UART Controller #0 (rev 20) 
0000:00:1e.3 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO SPI Controller #1 (rev 20) 
0000:00:1f.0 ISA bridge: Intel Corporation Tiger Lake-LP LPC Controller (rev 20) 
0000:00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20) 
0000:00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 20) 
0000:00:1f.5 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP SPI Controller (rev 20) 
0000:01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15) 
0000:02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter 
10000:e0:17.0 SATA controller: Intel Corporation Device a0d3 (rev 20) 


```

Plz let me know if you need more details

---

### Post by deadflowr on 2021-07-02
[s]The package is in the universe repository.
Which may not be enabled.
Try
```
sudo add-apt-repository universe
sudo apt update

```
Check if it outputs any errors.
If not try
```
sudo apt install uswsusp
```
If any issues come about post the outputs.
[/s]


OOPS, sorry, wrong release.
The uswsusp package is not available on 21.04,
It's only available for Ubuntu 18.04 and Ubuntu 20.04.
It's been removed for the newer 21.04 release.

Unfortunately, I do not know what alternatives are in place, if any.

---

### Post by ayzx2 on 2021-07-02
Thank you for your insight!
Do you know how can I enable hibernation in Ubuntu 21 if I can't install uswsusp

---

