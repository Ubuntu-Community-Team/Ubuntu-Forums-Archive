---
title: "Windows 7, Boot-Repair"
date: 2014-12-06
forum: Installation &amp; Upgrades
---

### Post by Riaz_Rahman on 2014-12-06
[http://paste.ubuntu.com/9398880/](http://paste.ubuntu.com/9398880/)


Hi,
I am trying to recover a lost Windows partition on my HP Envy 1030us Ultrabook. One day I turned on my machine only to find that the BIOS couldn't find an operating system to boot (Error [3F0 BootDevice not found]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/quot-Hard-Disk-3F0-BootDevice-not-found-quot-Error-Message/td-p/2443931")). I was previously running Windows 7 and never touched the OS or partitions, nor had I recently installed new hardware. After freaking out, I started Googling how to recover my data. I created an Ubuntu LiveUSB booted into it, and unfortunately my Windows partition wasn't showing up in GParted.  So I began to suspect that my Master Boot Record became corrupted? Next, I installed boot-repair in order to see if repairing the MBR would bring back my Windows and files. I didn't get the option for "Recommended repair" and only for "Create a BootInfo Summary." 

Above is a link to the report. Can someone please help interpret what's going on and if I'm approaching this problem the right way? Thanks!

---

### Post by oldfred on 2014-12-06
You are only showing two drives, a 32GB and 16GB.
I assume the 16GB is your flash drive as sdb/

Is this system an Ultraboot with a small (32GB) SSD and a larger hard drive. If so hard drive is not shown at all.
ata-LITEONIT_LMT-32L3M-HP_002228100866-> ../../sda 
usb-PNY_USB_2.0_FD_AA00000000002117-0:0 -> ../../sdb.

Does BIOS corretly show you have a larger hard drive? If not check for loose connections.

---

