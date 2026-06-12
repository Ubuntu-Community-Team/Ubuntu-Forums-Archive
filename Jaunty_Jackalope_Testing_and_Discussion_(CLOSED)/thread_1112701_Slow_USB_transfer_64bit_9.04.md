---
title: "Slow USB transfer 64bit 9.04"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LowSky on 2009-03-31
I have really slow transfer rates with my usb flash drive. using 9.04 64bit and yes my USB port is 2.0, USB transfer rates are 10 times faster in Windows 7, so I know it isn't a BIOS issue.

```
john@john-desktop:~$ lsmod
Module                  Size  Used by
usb_storage            93888  1 
binfmt_misc            18572  1 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65592  1 vfat
lp                     19588  0 
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              20112  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64028  0 
ppdev                  16904  0 
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
nvidia               8132632  36 
pcspkr                 11136  0 
serio_raw              14468  0 
parport_pc             45096  1 
parport                49584  3 lp,ppdev,parport_pc
usbhid                 47040  0 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
floppy                 75816  0 
vesafb                 15240  1 
fbcon                  49792  72 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```


```
john@john-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

```
john@john-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
```

---

### Post by Cybie257 on 2009-03-31
Not sure what could be going on. I've seen quite a few posts about complaints with slow USB in Linux. 

At this very moment, I am copying from an NTFS formatted 32GB USB Flash drive from Patriot to an Ext2 formatted 3-drive Raid-5 with a Gigabyte MOBO with an Intel Core2. Jaunty 64-bit with all the latest updates.

Speed: 25.2 - 25.7 MB/Sec

The other day I was copying from my windows (dual boot system) side to the Flash drive (Same exact Data). It's a 13GB VmWare image. Windows was going to take over 1 1/4 hours to copy that. Shut it down, booted in to windows and started the copy again. Took about 10 mins. 

strange. I've always had better performance with USB storage transfer rates within Linux (vs Windows).

The only suggestion I can think of is to check if Legacy mode (for USB) is enabled on your BIOS. Is so, try changing that and see what happens. 
EDIT: And since you mentioned not BIOS. It could be BIOS Settings vs Drivers...??? 

-Cybie

---

### Post by halfsane on 2009-03-31
Im in the same boat.. my USB 2.0 transfer speeds seem to be about half of what they are in vista on the same machine.

---

### Post by LowSky on 2009-03-31
> **Cybie257 said:**
> N
The only suggestion I can think of is to check if Legacy mode (for USB) is enabled on your BIOS. Is so, try changing that and see what happens. 
EDIT: And since you mentioned not BIOS. It could be BIOS Settings vs Drivers...??? 

-Cybie

yeah its set for legacy support. If it wasn't then I couldn't boot from USB

---

### Post by LowSky on 2009-04-01
Some extra information, I tried to copy a 1GB file to the flash drive and it fails at around 250MB. In Windows the file transfer works with no issue. This isn't a hardware issue, I'm using my Phenom x4 with 4GB of RAM a 700Mb file should take 5 minutes to load to a flash drive, and thats being generous.

Seems this issue is floating around the web but no real fix is mentioned. the issue goes back over 2-3 years for 64bit, and over multiple distros, not just Ubuntu. It seems things worked fine on 32bit in the orginal Hardy release, but not after the 8.04.1 update and there after. So I'm assuming its some its either a Kernel issue or something closly related to the Kernel that updated around the same time.

This is a real issue for me, because I need to transfer files from Flash drives ( as other means of portable storage are not as handy)and I dont have an hour or two to wait for a 500-2GB file to upload to the device. If its working in Windows XP and Windows 7 then I know it is not a direct hardware or BIOS setting issue, but Linux related.

Here is a just one of the link I found pertaining to the issue in Launchpad
[https://bugs.launchpad.net/ubuntu/+bug/177235](https://bugs.launchpad.net/ubuntu/+bug/177235)

and on the forum
[http://ubuntuforums.org/showthread.php?t=793688&page=12](http://ubuntuforums.org/showthread.php?t=793688&page=12)

---

### Post by LowSky on 2009-04-02
I guess this is a bump

 here is more awesome information on this complaint, its also effecting my Netbook using 8.10, I get transfer speeds of about 15MB/sec and they drop to about 8/9MB/sec

And no this isn't just on one udb flash drive, I tested it on 2 dfferent drives and two computers and got the same results.

USB is the defacto for portable drives, so why do we have this issue?

---

### Post by TrueTom on 2009-04-02
[https://bugs.launchpad.net/gvfs/+bug/197762]("https://bugs.launchpad.net/gvfs/+bug/197762")

---

### Post by LowSky on 2009-04-02
Thanks for the link it seems to be my issue exactly


I can't believe this isn't effecting more people, or do most of you think it takes minutes to copy 100MB to a USB drive?

---

### Post by xzero1 on 2009-04-02
Keep in mind that usb transfers and usb flash memory transfers are different issues, not to mention flash read and write speeds. 

Another problem is that the reported nautilus 'start' speeds are probably erroneous. As an example, if I test my drive's sequential read speed via 'hdparm -t...' I get around 17MB/sec. If I copy a file to this drive it starts at 25MB/sec and ends at around 13MB/sec. Write speed faster than seq read speed?? These start speeds are probably measuring 'burst' speeds which have little relation to a sustained transfer speed.

Interesting observations are made in this thread: [http://www.kessels.com/forum/index.php?topic=1425.0](http://www.kessels.com/forum/index.php?topic=1425.0)

Others seemed to have 'solved' the problem using different mounting options as shown here.

[http://www.linuxquestions.org/questions/linux-hardware-18/usb-2.0-slow-write-but-fast-read-solution-yet-500937/](http://www.linuxquestions.org/questions/linux-hardware-18/usb-2.0-slow-write-but-fast-read-solution-yet-500937/)



Still, if the kernel is using usb 1 instead of usb 2 it could be a moot point.

---

### Post by LowSky on 2009-04-06
I understand the whole thing of Flash drive being slower to write to than say a SATA hard drive, but when i'm getting 8MB/sec on a external hard drive as well I know the issue is more than just a flash drive issue.

I tried transfering the same 900+ MB file onto a drive and it still slower using Linux, while Windows (XP and 7) are much faster.


I'm going to try buy turning off the sync option from etc/fstab as one of your links suggests, lets see if that works

---

### Post by cariboo on 2009-04-06
I have always felt that slow usb transfers have something to do with Nuatilus. I have a 750Gb external drive connected to my server for backups. Running hdparm on the drive this is what I get:

```
sudo hdparm -tT /dev/sde
[sudo] password for jimk: 

/dev/sde:
 Timing cached reads:   990 MB in  2.00 seconds = 494.64 MB/sec
 Timing buffered disk reads:   86 MB in  3.03 seconds =  28.40 MB/sec
```

See the screenshot to see data transfer rates using mc.

Jim

---

### Post by mendres on 2009-04-06
So my question is, how do I disable sync mount option for the USB drive? As I know, Ubuntu mounts the disc via HAL daemon? How can I tell HAL to mount external discs without the sync option?

---

### Post by xzero1 on 2009-04-07
> So my question is, how do I disable sync mount option for the USB drive? As I know, Ubuntu mounts the disc via HAL daemon? How can I tell HAL to mount external discs without the sync option?Under the Volume tab of properties on your mounted drive click settings and you can change your mount options.

---

### Post by ronacc on 2009-04-07
I have in the last few days done a couple of installs of jaunty on my eeepc 701 4g , out of 10 attempts to install the netbook remix from a usbstick to an sdhc card only one succeded and all were horribly slow and most hung after some HOURS . an install of the april 3 daily of the regular i386 jaunty went better but was still very slow compared to installing from a cd (about 2 hrs) and updates are also slow installing ( the d/l part seems normal )  , this has not been the case with other versions (easypeasy and eeebuntu ) I have installed from usbstick to sdhc card which went faster than a cd install . I have screenlets running which monitor my cpu and ram ( 2gb ) and they are not nearly maxing out so that is not the problem . I was thinking this might be some sort of usb problem .

---

### Post by kvizz on 2009-04-19
> **LowSky said:**
> yeah its set for legacy support. If it wasn't then I couldn't boot from USB

this one was helpful for me
now it took 6 minutes to copy 4Gb to my usb stick, previously i was told "4 hours to go"

---

