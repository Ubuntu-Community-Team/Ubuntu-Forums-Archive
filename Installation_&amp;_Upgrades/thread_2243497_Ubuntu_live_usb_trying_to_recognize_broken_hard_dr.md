---
title: "Ubuntu live usb trying to recognize broken hard drive"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by kumareshy on 2014-09-09
Hello everybody,
I'm a long time user of ubuntu and I just ran into a problem with my laptop. My laptop HDD has become corrupted and I am unable to mount it or read any data from it, but I can see the partition table and the partitions and all that, So I booted into an ubuntu 14.04 live usb with persistence, But the live usb tries to recognize the hard drive for 20 minutes before booting the live usb. It just gives the same error again and again. Here's an excerpt from dmesg
[ 1125.724306] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1125.724314] ata1.00: irq_stat 0x40000001
[ 1125.724319] ata1.00: failed command: READ DMA
[ 1125.724326] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 12 dma 4096 in
[ 1125.724326]          res 51/40:00:00:00:00/00:00:00:00:00/00 Emask 0x9 (media error)
[ 1125.724329] ata1.00: status: { DRDY ERR }
[ 1125.724332] ata1.00: error: { UNC }
[ 1125.950521] ata1.00: configured for UDMA/133
[ 1125.950539] sd 0:0:0:0: [sda] Unhandled sense code
[ 1125.950543] sd 0:0:0:0: [sda]  
[ 1125.950545] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1125.950548] sd 0:0:0:0: [sda]  
[ 1125.950550] Sense Key : Medium Error [current] [descriptor]
[ 1125.950554] Descriptor sense data with sense descriptors (in hex):
[ 1125.950556]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1125.950566]         00 00 00 00 
[ 1125.950570] sd 0:0:0:0: [sda]  
[ 1125.950573] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1125.950576] sd 0:0:0:0: [sda] CDB: 
[ 1125.950578] Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1125.950587] end_request: I/O error, dev sda, sector 0
[ 1125.950592] Buffer I/O error on device sda, logical block 0
[ 1125.950609] ata1: EH complete
I'm currently posting this from my live usb. What do I do to prevent it from seeing my dead hard disk and trying to read it ? If you need any additional data, Please give me a request.

---

### Post by cogier2 on 2014-09-09
You could install another drive as the primary and the HDD as a secondary drive so that the Live USB wont look for it, or you could take the HDD out of your computer and plug it into another, again as a secondary drive. Alternatively get a hard drive dock ([Like this]("http://www.dabs.com/products/akasa-duodock-x-superspeed-usb-3-0-dual-bay-dock-2-5-3-5--sata-blk-90M5.html?src=3"))

---

### Post by kumareshy on 2014-09-09
I can't do any of those things with this laptop :(:mad:

---

### Post by Mark Phelps on 2014-09-09
You need to press the Function key on your laptop that allows you to select the boot device.  IT varies by machine but it's typically F9 or F12.

---

### Post by kumareshy on 2014-09-10
I can already boot into the ubuntu live usb. But the problem is that once I select try ubuntu without installing, It scans all the hardware in my computer, including the hard drive. But it's dead, So it just keeps on trying for 20 minutes before giving up and turning on. On my first go, it didn't take long and booted quickly. The partitions were also visible. But I couldn't mount them. Now, I can't even see the partition in the file browser and Gparted can't read the partition table, But photorec and testdisk can see all my partitions. How can I prevent ubuntu from trying to see my hard disk ?

---

