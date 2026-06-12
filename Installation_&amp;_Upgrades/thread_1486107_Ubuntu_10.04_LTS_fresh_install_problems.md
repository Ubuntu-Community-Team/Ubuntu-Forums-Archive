---
title: "Ubuntu 10.04 LTS fresh install problems"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by ananth.v on 2010-05-17
Hi All,
 
I am trying to install Ubuntu 10.04 LTS after burning the iso file downloaded from the site to a CD. I am doing this on an old laptop Compaq Presario V2000.
 
As many have noted, the install freezes after showing the 'keyboard = human' icon. Saw exactly the same problem as [http://ubuntuforums.org/showthread.php?t=1466190](http://ubuntuforums.org/showthread.php?t=1466190), but there has been no solutions for it yet.
 
Pressing any key as soon as the icon appears shows few options like 'try ubuntu..', 'install ...', etc. but nothing happens when i click enter on selecting the option, it just hangs. The hard drive light keeps blinking though.
 
I had dual boot ubuntu 8.10 and windows 2000 earlier, tried upgrading to winXP, but the product key i had did not work and could not boot to either older win2000 or ubuntu 8.10 after that :( (maybe xp overwrote the boot sector or something like that), therefore tried to install ubuntu 10.04, but this too is not working as the installation is hanging. Now, when i boot up the system without any installation cd (winxp or ubuntu), grub screen does not show. As a result, i am not able to boot into any OS.
 
Googled for this problem, saw a few solutions which suggests selecting 'try ubuntu without installing' and selecting 'i915.modeset=1 xforcevesa', but all these involve upgrading from previous ubuntu versions, but i dont think i can try this as there is no other OS in the laptop (posting this from somewhere else as i cant access internet at home).
 
[http://ubuntuforums.org/showthread.php?p=9219366#4](http://ubuntuforums.org/showthread.php?p=9219366#4)
[http://ubuntuforums.org/showthread.php?t=1463294&page=2#14](http://ubuntuforums.org/showthread.php?t=1463294&page=2#14)
 
Could someone please help me with it? Can i altleast try to boot to the previous ubuntu 8.10 somehow? please advise.

---

### Post by darkod on 2010-05-17
When you hit any key to get the options shown, then hit F6 for more advanced options. It should show you the boot commands I think. Use the arrows keys and the End key to get the cursor at the end of the line and add nomodeset

Press Ctrl + X to boot (I think that should work).

Or if F6 shows you option like Safe Graphics, select that. After that Try Ubuntu if it brings you back to that menu. If that worked, a video driver is the problem.

You can continue and install, but the first login you will have to do the same to boot successfully. After you have booted the hdd ubuntu, it should locate drivers itself and offer to update them. Hopefully that should resolve it.

PS. If you prefer to try saving the 8.10 first, look here how to reinstall grub1 to the MBR:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But be careful, you will need a cd from 8.10 or 9.04, not later, and use the instructions for grub1, 9.04 or earlier version. This is because 9.10 started shipping with grub2 which works differently.

---

### Post by DougieFresh4U on 2010-05-17
Have you tried to boot the 'live-cd'? Put the cd in and let it go through it's thing until you are presented with desktop?
Also, can you get a copy of the Karmic 9.10 cd, burn a copy from another computer.

---

### Post by ananth.v on 2010-05-17
darkod, thanks for the instructions, i'll try it and let you know what happens.
 
DougieFresh4U, i tried that first before going for the install. but it hangs at the same place (at the 'keyboard = human' icon).

---

### Post by ronparent on 2010-05-17
Also consider trying some of the other boot options brought up by f6. An older system might need noapic nolapic as well as nomodeset. It is a matter of trial and error to pin down the boot options you may need. 

Also, if you delete the quiet splash from the boot line referred to by darkod, you will be able to see the boot commands executed. In general, the sooner in the boot process your boot locks up, the more likely the earlier boot choices will need to be applied. You will probably need further instruction to make the boot options permanent once the system is installed.

---

### Post by ananth.v on 2010-05-18
ronparent, thanks. tried that. it did work, but have not been able to fully install. here are the things i did.
1. set noapic, nolopic and nomodeset, removed 'quiet splash' and selected 'try ubuntu'. took a long time, but it went to the desktop. clicked on 'install ubuntu' on the desktop, did not work.
 
2. rebooted and with the same options, selected 'install ubuntu'. it gave options to select language, keyboard etc., but failed in between giving the error 'ubi-language crashed' but also gave an option to 'continue anyway'. clicked that and continued, but as soon it came to the partitioning, it jumped back to the screen where it asks for user name, user id and password, strange. at the same time, it gave an error 'ubi-migrationassistant crashed'.
 
3. thought this could be due to the 'only-ubiquity' boot option. so, removed this option in the boot command and selected 'install ubuntu'. but still booted the live cd. anyway, once the desktop showed up, double clicked on the 'install ubuntu' icon and started the process. this didnt give any 'ubi-' errors but when it went to the partition step (last step), it failed giving an error and asked to try with a boot cd that is written at a lower speed.
 
all along, either with try ubuntu or install ubuntu option, the terminal showed several errors, like ureadahead errors, I/O errors, etc.
 
So, it seems that it will work, will try to create a cd writing it at lowest speed and post the results.

---

### Post by darkod on 2010-05-18
The install cd should not be burned at more than 8x, even better at 4x.

You can also try with the Alternative Install CD (image). The installer is text based but you end up with the same system.

But even if the install succeeds that way, the first boot might still need parameters like nomoset, noapic, etc. Depending what is the problem right now. Just a bad cd, or something else.

---

### Post by efflandt on 2010-05-18
You may have issues even if you get it to install, or at least I do with a Presario V2000 laptop from somewhere around 2005 (it came with WinXP).  For 10.04 I would certainly suggest hitting a key when you see the first graphics at the bottom of the screen from install CD and try removing **quiet splash** parameters and adding **nomodeset**, so you can hopefully see what is happening when attempting to boot a live system from the CD.  The "nomodeset" would use user space video instead of the new kernel mode setting (KMS).  I seem to remember it having ATI 200M video.

I currently have it dual booting WinXP home and Ubuntu 9.10, but have some issues which may be hardware failing, because it was previously the only computer somebody had.  One issue is even getting it to turn on, not sure if due to power supply/cable/connector or that Linux suspend and hibernate fail (with no errors in logs).  Actually it appears to go into suspend or hibernate from Linux, but wakes to a blank screen with no backlight and unresponsive (and nothing in logs about waking).

Another issue is that keyboard and mousepad input is sometimes erratic. Keypresses do not always go through, so passwords can be difficult (especially with no feedback, like sudo).  And the mousepad can be alternately laggy and jumpy.

But I don't know how much of that is due to limited support for little used hardware at the bottom of the price scale, or due to some other mechanical deterioration.  It does have a newer WD 160 GB hard drive from after the original drive failed about a year ago, and RAM upgraded to something over 1 GB.  But problems getting it to turn on, the keyboard/mouse lag, and lack of suspend/hibernate could make it frustrating.

PS: I brought it home tonight and my Compaq Presario V2000 boots 10.04 LTS fine from CD using just the **nomodeset** kernel parameter.  Maybe my starting issue is a bad battery, because I can only boot if I remove the battery and hold the power button for 5 seconds on AC power.  Keyboard seems to work fine, but mouse pad still lags and jumps, and mouse pad button works more reliably than double tap.  I don't know if wireless works. because I cannot seem to activate Broadcom B43 from the CD. So I am temporarily using an old Linksys WET11 to post this from the CD on that computer.

This is hardware from lspci:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
```

free
```
             total       used       free     shared    buffers     cached
Mem:       1154896     981104     173792          0     135564     582644
-/+ buffers/cache:     262896     892000
Swap:      2096472          0    2096472
```

---

### Post by efflandt on 2010-05-19
Since I installed 10.04 LTS on the hard drive of the Presario V2000, so far everything works great, better than 9.10 it seems.  Maybe the battery was weak or the new installation cleared up whatever suspend/hibernate in 9.10 mangled, because now that the battery is charged, it starts to boot right away, and keyboard and mouse pad lag is minimal most of the time.  Wireless works after activating Broadcom B43 (with stronger signal than newer Dell Inspiron 6400 using Broadcom STA).

I don't know if the nomodeset parameter is necessary, but since the OP had a problem even booting the install CD and I don't, I plugged that into /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset"

I have not tried suspend or hibernate yet, but am happy with the way it is working so far.

[posted from 10.04 LTS on internal drive of Presario V2000]

---

### Post by pranavdes on 2010-05-19
I have been having similar problems with my IBM thinkpad R51. I cannot go to try Ubuntu as the minimum RAM neeeded for it is about 384 MB and I have 256 Megs. I did try install ubuntu with various options mentioned above already. What is also interesting is if I specify vga=311/771 or any other mode the machine freezes in text mode. just after starting some sensor module. If I remove vga option all together it goes into GUI mode (change in resoultion and blank screen) but freezes there. I had 9.04 installed earlier on the same machine with no problems during the installation procedure. any suggestions on this predicament?

PS: I have quiet and flash removed.

---

### Post by pranavdes on 2010-05-19
I have managed to find the solution to my problem. Just needed to set i915.modeset=1 in boot command for installation (also for booting into the system).

---

### Post by ananth.v on 2010-05-19
I couldnt install 10.04 yet, but did this:
 
1. booted into the 'try ubuntu' and downloaded ubuntu 9.10
2. created a partition and placed the ubuntu 9.10 iso there.
3. installed unetbootin and ran it to install 9.10 from that partition. i could have installed 10.04 using the same method, but was not sure because it is giving problems, maybe will wait for the next release.
 
but when i boot to 9.10, there is an icon on the desktop to 'install ubuntu', showing that it is actually a live cd boot. is this correct? will need to look into it further..

---

