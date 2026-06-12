---
title: "black screen after automatic update (hp laptop)"
date: 2015-08-26
forum: Installation &amp; Upgrades
---

### Post by docdoc2 on 2015-08-26
I didnt use my laptop for the last 3 weeks, so yesterday ubuntu did the update of some stuff, just normal, ith thought. but today, after fresh boot, i get the grub and then the normal loading screen and then BLACK. also, no cpu activity.

I tried to start under 'advanced' in the grub with an old generic and selected the oldest, and voila, it started again.

but still i am clueluss how to use the updated version now

lspci:
> 00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev a1)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
0a:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)




---

### Post by ubfan1 on 2015-08-26
Looks like a video problem with the Nvidia (guessing the 304.125 driver for you hw).  Try starting the new kernel, and switch to a virtual terminal with ctrl-alt-F2  and see if you get a login prompt (text).  Login and try running:
sudo apt-get install --reinstall nvidia-304
(check the package name for your situation)
At least any errors building the package will show up when you do this.

---

### Post by ajgreeny on 2015-08-26
There is obviously a problem with running the newest kernel with your hardware, so let's find out where we are at present.

Boot into the kernel that works and look to see what kernels you have on the system by running command ```
ls /boot | grep vmlinuz
``` The top one in the list will be the one that is not booting. You can also see what packages were updated most recently by running command ```
grep -iw upgrade /var/log/dpkg.log.1 /var/log/dpkg.log
``` That will list all upgraded packages by the date of upgrade, though you may need to use ```
grep -iw install /var/log/dpkg.log.1 /var/log/dpkg.log
``` as new kernels will be a new package install, not an upgrade.

Let's see what the situation is before we attempt to tell you which way to solve this permanently.

---

### Post by docdoc2 on 2015-08-27
Thank you very much. Putting the nvidia back to 304 helped. The new one was more of a downgrade for me

---

### Post by ajgreeny on 2015-08-28
Great!
Please mark this as SOLVED from the Thread Tools menu at the top.

---

