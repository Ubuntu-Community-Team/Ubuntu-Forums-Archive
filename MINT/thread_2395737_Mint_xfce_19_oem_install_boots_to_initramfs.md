---
title: "Mint xfce 19 oem install boots to initramfs"
date: 2018-07-06
forum: MINT
---

### Post by 3dgraphdav on 2018-07-06
I had 18.3 oem 64 bit install and it worked good. (stayed on the temporary user part)
Wanted to do a fresh OEM install for 19 64 bit and it keeps booting to busy box
have looked around and nothing that I have tried has worked
Able to use multibootusb drive to boot into live and also used it to do oem install
Using oem because I was working on this computer for a friend and they haven't picked it up yet. I've been using the Linux side and wanted to do an upgrade

This is a Sony Vaio core 2 duo with 4GB ram
Hard Drive is partitioned into
sda1 Windows recovery
sda2 windows
sda3 Extended
sda5 Mint
sda6 swap

```

System: Host: mint Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0 Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Linux Mint 19 Tara Machine: Device: laptop System: Sony product: VGN-NW125J v: C601FG7G serial: N/A Mobo: Sony model: VAIO serial: N/A BIOS: American Megatrends v: R0170Y4 date: 05/22/2009 Battery BAT0: charge: 28.0 Wh 94.2% condition: 29.7/41.1 Wh (72%) model: Sony status: Charging CPU: Dual core Intel Core2 Duo T6500 (-MCP-) arch: Penryn rev.10 cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4_1 ssse3) bmips: 8372 clock speeds: max: 2100 MHz 1: 1308 MHz 2: 1537 MHz Graphics: Card: Intel Mobile 4 Series Integrated Graphics Controller bus-ID: 00:02.0 Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa) Resolution: 1366x768@59.94hz OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express version: 2.1 Mesa 18.0.0-rc5 Direct Render: Yes Audio: Card Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic Network: Card-1: Marvell 88E8057 PCI-E Gigabit Ethernet Controller driver: sky2 v: 1.30 port: d000 bus-ID: 01:00.0 IF: enp1s0 state: down mac: <filter> Card-2: Intel WiFi Link 5100 driver: iwlwifi bus-ID: 02:00.0 IF: wlp2s0 state: up mac: <filter> Drives: HDD Total Size: 328.1GB (2.4% used) ID-1: /dev/sda model: Hitachi_HTS54323 size: 320.1GB temp: 0C ID-2: USB /dev/sdb model: SanDisk_Cruzer size: 8.0GB temp: 0C Partition: ID-1: / size: 1.9G used: 221M (12%) fs: overlay dev: N/A ID-2: swap-1 size: 4.13GB used: 0.00GB (0%) fs: swap dev: /dev/sda6 RAID: No RAID devices: /proc/mdstat, md_mod kernel module present Sensors: System Temperatures: cpu: 56.0C mobo: 56.0C Fan Speeds (in rpm): cpu: N/A Info: Processes: 172 Uptime: 2:01 Memory: 1116.6/3786.5MB Init: systemd runlevel: 5 Gcc sys: 7.3.0 Client: Shell (bash 4.4.191) inxi: 2.3.56 
```

---

### Post by yancek on 2018-07-06
THe partition info you show has two windows partitions, which version?  You show a Mint install on sda5 so did you successfully(?) complete the install and now cannot boot it or are you unable to boot the Mint installer?  Since there is an instance of windows, does it boot?  If you have the usb with Mint on it, you might go to the boot repair site at the link below, download and run it per instructions.  Be sure to select the Create BootInfo Summary option.  When it finishes, it will show a link which you can post here which will show more details and someone may be able to help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 3dgraphdav on 2018-07-06
The windows version is vista. (I dont use it) The mint one is the new mint Xfce 19 "Tara" I completed the install. It boots to grub then when slecteing Linux Mint it starts to boot then drops to a terminal. I tried the boot repair and it didnt fix it. I have read about it might be aa bad super block. ( don't know what that is. Is it a block of data on the drive?) followed the instructions and moving to a different one didnt help
here is a picture of what happens
The uuid is the usb that I installed mint from

---

### Post by yancek on 2018-07-07
Can't help without more information from boot repair and you did not post a link to the output.  The image in your last post shows it is looking for a windows FAT32 partition.  Don't know any reason why it would need to do that unless you had an EFI install of Mint.

---

### Post by 3dgraphdav on 2018-07-07
I apologize. Thank you for taking your time to help me. I had ran the boot repair 2 times before posting here and didn't save the url. but after that I reinstalled the os the regular way. (not oem) Still same problum. This was all before posting here. I just ran the boot repair again and here is the output. Also did try the windows side and it wants to run system repair.  I let it run and went to bed. When I woke the next morning it was at the termail screen again. Tried again later and it said couldn't repair.  Windows just tries to boot but just kicks back to the start. then the grub menu
[http://paste.ubuntu.com/p/s5FPhyBk96/](http://paste.ubuntu.com/p/s5FPhyBk96/)

---

### Post by 3dgraphdav on 2018-07-08
Was wondering if the problem could be how I installed it. You said that it is looking for a fat32 partition. Might have installed using EFI.  I'm using a usb with multibootusb installed on it.  http://multibootusb.org/
It is written to install multiple live CD images  on a usb.
 I have used it to install mint 18.1- 3 and Ubuntu - mate to the usb and installed the systems to computers from that usb with no issues 

It has a syslink (I think that's the name) boot and a grub2 boot menu. So I tried to install using oem again using the grub2 menu. Now it won't even boot. I went to advanced options during boot and then recovery options. It boots back to the shell and I ran the output like in the previous image. Cat /proc/cmdline  in the output it says about the live boot and shows multibootusb

Could the reason be because I installed the iso to the usb using this program instead of directly writing it like normal?

---

### Post by 3dgraphdav on 2018-07-09
My guess was right.  I wrote the iso directly to the usb and reinstalled using OEM and now it boots. Everything works on the linux side. Just can't get windows to boot yet.

---

### Post by yancek on 2018-07-09
What does happen when you select vista from the boot menu?  Do you see vista on the boot menu?  Check the /boot/grub/grub.cfg file to see if there is  windows entry.  If not, run:  sudo update-grub and watch the output.  If that still doesn't work, run boot repair again and post the link, someone may see a problem.

I'm not sure what your original problem was.  I"ve only tried using multiboot once so am not familiar with how it works.

---

