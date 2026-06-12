---
title: "Small upgrade broke Ubuntu"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by MadeOfEyelashes on 2010-10-23
I did a fresh install of 10.10 x86 on my HP DV2988se, all was working fine (except my internet takes forever to connect, but that's not a big deal). But I did a normal upgrade and had to restart Ubuntu. 

When I came back my laptop kind of freezes. I say kind of because I can still move my mouse, I still see the seconds ticking on the clock, and I see the network attempting to connect to the internet. However, I can't interact with them. There is something asking for my password when I sign on (after the log in screen) and I can't interact with that either. Also, I can hover over the icons on the top and it will tell me what it is, but I can't click on them...


Any suggestions?

**Edit: **When I run it in failsafe graphics mode everything works fine (except my compiz effects) Also, I noticed that the indicator that my wireless is on keeps flashing between the on and off colours (I'm not sure if this is normal, or just in failsafe graphics mode though)

---

### Post by P4man on 2010-10-23
can you tell us more about the machine? Provide output of
```
lspci
```
SOunds like a problem with  X/ the videodriver. The update must have provided you with a new kernel, so Im guessing you are using kernel drivers?

---

### Post by MadeOfEyelashes on 2010-10-23
I attempted to get back on in fail safe mode, but now I'm having the same problem there, so I tried to type it in the terminal without any sort of gui but I couldn't scroll up to read the whole thing :(

Suggestions?

Edit: yes I am using the kernel drivers

---

### Post by P4man on 2010-10-23
I just googled your laptop, you seem to have an intel x3100. No need for anything other than kernel drivers and I actually doubt that is causing the issue, but since I have the same GPU in a very similar HP laptop I will know soon as Im installing the updates with the new kernel now. 

Meanwhile, do you have a liveCD at hand? can you boot it, mount the internal drive and locate /media/yourlaptopdrive/var/log/Xorg.0.log and attach it?

edit: been using 2.6.35-22 for a short while now, no problems on my X3100. Everything seems to work like it used to, including desktop effects.

---

### Post by MadeOfEyelashes on 2010-10-24
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


that's what I got from lspci from my livecd

---

### Post by P4man on 2010-10-24
Yeah, same video processor as me, works fine here. You didnt try to install amd or nvidia drivers by any chance?

If you can, try booting recovery mode. Right after the bios loaded, press the shift key to bring up grub boot menu (if it doesnt show by default). Then select ubuntu-whatever-(recovery mode). In the next menu, press down key until you select Root (drop to root shell). In that shell, execute this command:

```

mv /etc/X11/xorg.conf /etc/X11/xorg.backup
```

That alone might fix it,  but do this as well:

```
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

then type reboot to reboot and cross fingers.

---

### Post by MadeOfEyelashes on 2010-10-24
I tried to do the first command but it said cannot start '/etc/x11/xorg.conf': no such file or directory

---

### Post by P4man on 2010-10-24
Note the upcase in **X**11. But if you wrote it correctly and the file doesnt exist, thats okay. Just do the second one

---

### Post by MadeOfEyelashes on 2010-10-24
I did capital, I just didn't type it like that here (sorry, typing on my phone >.<)

I also tried doing the second command, yet I still have the same problem :(

---

