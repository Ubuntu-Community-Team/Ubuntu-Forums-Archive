---
title: "Nvidia drivers"
date: 2015-01-11
forum: Installation &amp; Upgrades
---

### Post by wonjun on 2015-01-11
Hello,

I'm currently using Ubuntu 14.04. Today I downloaded bootchart (to get help.  [http://ubuntuforums.org/showthread.php?t=2260134](http://ubuntuforums.org/showthread.php?t=2260134)) and had changed the option of using a different driver for my Video card. (See the attached file. I booted this from the usb)

I ticked the first option (I was using the second option as shown in the pic) and it took a while to set up, due to slow connection from the internet.

But after that - I restarted, and it loaded the grub screen. After that, it shows "ubuntu" - and the screen goes blank.
Is it because I changed the driver for my Video card?

Can someone help me?

---

### Post by MAFoElffen on 2015-01-11
Please post the results of:
```

sudo lspci -vvn | grep -i VGA
sudo lshw -numeric -class video

```
Also post your /var/log/Xorg.0.log file

And you said you downloaded and used bootchart... but I am still waiting for you to post the results of that in that other thread you have going...

---

### Post by tokyobadger on 2015-01-12
[quote="wonjun"]I ticked the first option (I was using the second option as shown in the  pic) and it took a while to set up, due to slow connection from the  internet.[/quote]
In that particular screenshot you have no internet connection... try the 331 updates (if your card is new enough - see below)

Would help if you gave more info on your hardware - from the screenshot it looks like a laptop - without even knowing your gpu model we can't say whether you should be on the nvidia legacy drivers or the latest or addressing a hybrid gfx situation.

---

### Post by MAFoElffen on 2015-01-12
Another request for your info on both your threads. Please put them in or attached to a post in the appropriate threads.

Hard to help you without feedback.

---

### Post by efflandt on 2015-01-12
It looks like you may be booting a live/install iso. In that case you cannot install any video drivers, kernel updates, or anything else that initially happens during boot, because the initial boot is on a fixed squashfs (compressed) file system. Although, if you created the live/install on USB with persistence you can add other programs that run after booting.

Once you install a regular system somewhere, then you can add/change video drivers in that (assuming that you have an Internet connection at the time).

---

### Post by MAFoElffen on 2015-01-13
In the first post, the OP said after that screen shot on his own PC, he selected the fist option (NVidia driver instead of Nouveau). After that install, he said that ended at a black screen...

But the OP has not provided any feedback since. Nothing we can do yet.

If he does come back with the the info, we would could see what hardware he has and where the log says it had a problem, when it black screened. Then we could tell him to looked at his install system's disk and rename the /etc/X11/xorg.conf file to anything other than it's own name... (add ".old" as an extension) Then he could reboot and it would use the Neuveau driver again... but he wouldn't get a black scree like he is now.

He has another thread open for a slow boot. Same there, waiting on his return and feedback. I can now see that his slow boot might be related to not having NVidia drivers pointing to his card... That would be fatser than letting xorg try and search different driver until IT decides what to use...

---

### Post by wonjun on 2015-01-13
Thanks for your quick replies. 
I deleted the drivers via ctrl + alt + F1 and then going from there - and it worked fine. And then I tried installing the latest drivers for my video card, but it created a mess with low graphics. 
(as answered here by Taz D   [http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver](http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver))
From there - I tweaked abit. (The file @ /etc/lightdm/lightdm.conf was blank in the first place, so I left it blank)
and used the command sudo apt-get install nvidia-current,

and it started working just fine.

I hope everything's back to normal.
Anyhow, these are the results of the commands that you requested.


sudo lspci -vvn | grep -i VGA
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
00:02.0 0300: 8086:0166 (rev 09) (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+






sudo lshw -numeric -class video
 *-display               
       description: 3D controller
       product: GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10DE:1140]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller [8086:166]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)

---

