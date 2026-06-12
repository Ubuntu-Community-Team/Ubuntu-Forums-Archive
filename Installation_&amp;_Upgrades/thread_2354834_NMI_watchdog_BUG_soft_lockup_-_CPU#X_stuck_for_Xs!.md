---
title: "NMI watchdog: BUG: soft lockup - CPU#X stuck for Xs!"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2017-03-07
Hi all,
   I had a well running installation of Ubuntu-Mate 16.04 on a workstation with 8TB raid / 2 x Nvidia GPU 1070 / 128 GB RAM. When configuring some of the RAM for temporal storage the system crashed and I was unable to recover it. 

    I thus tried to boot Ubuntu Mate 16.04 from an USB stick and received the error message "NMI watchdog: BUG: soft lockup - CPU#X stuck for 10s" with X running from 0 to 7. This message repeats forever. I then tried booting plain Ubuntu 16.04 with the same outcome. Finally, I could boot Ubuntu 14.04 without receiving this message but I want to install again the more recent version. 

What might be incompatible between my hardware and ubuntu(-mate) 16.04? How can I install it? What is the reason for this problem? I found some posts on this error message but none was related to the version of Ubuntu installed. I am aware that the Nvidia cards may be involved but when booting from the USB stick no driver is yet installed and still I get the error.....
Thanks for hints, D-E

---

### Post by Saxphile on 2017-03-07
I don't have a solution for you, but I am running into the same issue. Brand new computer (i7-7700K + 2 x GTX 1080 + 64GB RAM) that runs Windows 10 without any issues cannot boot using 16.10 or 17.04 alpha 2 from USB drive. All the information I have found is related to people getting this error message after their computers crash--not prior to installation.

---

### Post by dieter-erich on 2017-03-14
Hi,
   Still no progress: I have now tried running ubuntu-16.04, ubuntu-mate-16.04, ubuntu-mate-14.04, and plain ubuntu-14.04 from stick and the only one that definitely run was the latter. I could also install Debian but I need a release that has all the features that are necessary to run GPU acceleration.... 
Again, help is greatly appreciated....
D-E

---

### Post by jqgatsby on 2017-03-27
I am running into the same or similar problem. Here's a transcription of the error logs while trying to reinstall Ubuntu 16.04 on a new system76 laptop (the laptop boots fine when not trying to use the usb stick to reinstall):
[    3.383577] mmc0: Unknown controller version (3). You may experience problems
[    3.491328] nouveau 0000:01:00.0 priv: HUB0: 00d054 00000007 (19408216)
[    3.495643] noveau 0000:01:00.0: i2c: aux 0007: begin idle timeout 01109000
[    3.654967] nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22
[    3.744933] scsi host4: runtime PM trying to activate child device host4 but parent (1-3:1.0) is not active
[   32.097315] NMI watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [migration/0:9]
[   32.097360] NMI watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [migration/1:15]
[   32.101342] NMI watchdog: BUG: soft lockup - CPU#3 stuck for 22s! [migration/3:27]
[   32.101360] NMI watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [systemd-udevd:207]
[   32.105292] NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [migration/5:39]
[   32.105322] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [migration/4:33]
[   32.109338] NMI watchdog: BUG: soft lockup - CPU#6 stuck for 22s! [migration/6:45]
[   32.109342] NMI watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [migration/7:51]
[   60.097373] NMI watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [migration/1:15]
[   60.097349] NMI watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [migration/0:9]
[   60.101336] NMI watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [systemd-udevd:207]
[   60.101350] NMI watchdog: BUG: soft lockup - CPU#3 stuck for 22s! [migration/3:27]
[   60.105309] NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [migration/5:39]
[   60.105394] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [migration/4:33]
[   60.109331] NMI watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [migration/7:51]
[   60.109340] NMI watchdog: BUG: soft lockup - CPU#6 stuck for 22s! [migration/6:45]
[   60.901376] INFO: rcu_sched self-detected stall on CPU
[   64.901401] p2-...: (14999 ticks this GP) idle=f39/14000000000001/0 softirq=309/309 fqs=48

I should add that my laptop came with this configuration:
Ubuntu 16.10 (64-bit)
17.3&#8243; Matte HiDPI 4K HiDPI Matte Display
16 GB Dual GTX 1080 with 5120 CUDA Cores
4.5 GHz i7-7700K (4.2 up to 4.5 GHz &#8211; 8MB Cache &#8211; 4 Cores &#8211; 8 Threads)
64 GB Dual Channel DDR4 at 2400MHz (4× 16 GB)
1 TB NVMe PCIe M.2 SSD
No Additional M.2 Drive
No Additional 2.5&#8243; Drive
No Additional 2.5&#8243; Drive
United States Keyboard
WiFi up to 867 Mbps + Bluetooth
660 Watt Charger

Please let me know if there are any diagnostic commands I can run that would be helpful. I can still boot into the ubuntu version that's already installed, I just can't reinstall.

---

### Post by april-system76 on 2017-03-31
Hi all,

You can usually get around this issue caused by Nvidia/Nouveau weirdness at boot by using the boot parameter 'nomodeset' when installing, and on first boot after installation. When booting the live disk (in UEFI mode), you'll get a GRUB menu. Go ahead and select 'Install Ubuntu' and press `e` to edit GRUB before boot. Change the `linux` line:


```
linux    /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
```
to:
```
linux    /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash nomodeset vga=791 ---
```

So, you're just appending it to the `linux` line. Press F10 to boot in this configuration. **You might need to do the same thing after the initial boot.** In one case (a Sys76 Bonobo) we had to boot using Recovery Mode, enable networking, then resume normal boot where we could install the Nvidia drivers from our repository, though you could certainly use the graphics-drivers Nvidia repo as well. After installing Nvidia drivers, the system would reboot without issue.

Good luck, and happy computing :)

---

### Post by dieter-erich on 2017-04-01
Hi april-system76, 				 				 					 						 	
   thanks a lot for pointing out this solution! I'll try it from a stick first! Do you have any idea why the problem DOES NOT SHOW UP with plain Ubuntu-14.04 but does so with Ubuntu-16.04, Mate-14.04 and Mate-16.04? 
best, D-E

---

### Post by april-system76 on 2017-04-05
Hi Dieter-Erich,

My guess is something with the init system change from upstart to systemd, but this is wild speculation on my part :)

---

### Post by liuvay on 2017-05-30
Hi
I am running the same issue. Now I can boot into with your method, but now can not find the disk to install.
Dell Alienware i7 7700 cpu, GTX 1071 GPU, 521G SSD with win10, and 1T HDD.
[IMG]http://forum.ubuntu.org.cn/download/file.php?id=183366&t=1[/IMG]

---

### Post by alekeagle on 2017-12-08
I am getting the same error running the newest ubuntu for x86 and I get the cannot access perfct msr popup and then won't boot from disk when I don't install using bochs android emulator with i7 4370hz (I think) and won't boot with newest version of limbo x86 qemu

---

