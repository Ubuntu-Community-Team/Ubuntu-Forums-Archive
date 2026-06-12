---
title: "File Copying *Extremely* Slow"
date: 2009-06-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fifth on 2009-06-01
If been having problems with file copies taking forever. I initially thought it was a KDE problem since deleting to trash random small files and empty folders just piled notifications into the system tray which take many minutes to finish.

I've tried copying a 3 x 350mb file from a terminal, the first two files copied ok but the third started about 20 minutes ago ... and still going.

System monitor shows 'cp' as 'Disk Sleep' under CPU %.

I'm running an upgraded Jaunty with ext3 on all partitions.

Anybody any ideas or experiencing the same?

---

### Post by Wiebelhaus on 2009-06-01
Could you post your hardinfo here?

```
sudo apt-get install hardinfo
```
```

hardinfo
```

Save as file and post in code box please.

---

### Post by Wiebelhaus on 2009-06-01
Also slow performance is indicative of a failing drive as I'm sure you know...

---

### Post by fifth on 2009-06-01
> **Wiebelhaus said:**
> Could you post your hardinfo here?

```
sudo apt-get install hardinfo
```
```

hardinfo
```

Save as file and post in code box please.

```

Computer
  Summary
  Computer
  Processor  2x Intel(R) Core(TM) Duo CPU L2500 @ 1.83GHz
  Memory  3088MB (503MB used)
  Operating System  Ubuntu karmic (development branch)
  User Name  user (User)
  Date/Time  Mon 01 Jun 2009 20:20:43 BST
  Display
  Resolution  1024x768 pixels
  OpenGL Renderer  Mesa DRI Intel(R) 945GM GEM 20090418 2009Q1 x86/MMX/SSE2
  X11 Vendor  The X.Org Foundation
  Multimedia
  Audio Adapter  HDA-Intel - HDA Intel
  Input Devices
   Power Button
   Lid Switch
   Sleep Button
   Macintosh mouse button emulation
   AT Translated Set 2 keyboard
   PC Speaker
   Video Bus
   ThinkPad Extra Buttons
   TPPS/2 IBM TrackPoint
   HDA Digital PCBeep
  Printers
  No printers found
  IDE Disks
  SCSI Disks
  ATA WDC WD2500BEVS-0
  Operating System
  Version
  Kernel  Linux 2.6.30-6-generic (i686)
  Compiled  #7-Ubuntu SMP Fri May 22 04:54:08 UTC 2009
  C Library  GNU C Library version 2.9 (stable)
  Distribution  Ubuntu karmic (development branch)
  Current Session
  Computer Name  black-lap
  User Name  user (User)
  Home Directory  /home/user
  Desktop Environment  Unknown (Window Manager: KWin)
  Misc
  Uptime  4 hours, 17 minutes
  Load Average  0.37, 0.18, 0.18
  Kernel Modules
  Loaded Modules
  nls_iso8859_1
  nls_cp437
  vfat  VFAT filesystem support
  fat
  usb_storage  USB Mass Storage driver for Linux
  binfmt_misc
  ppdev
  bridge
  stp
  bnep  Bluetooth BNEP ver 1.3
  lp
  parport
  snd_hda_codec_analog  Analog Devices HD-audio codec
  arc4  ARC4 Cipher Algorithm
  snd_hda_intel  Intel HDA driver
  snd_hda_codec  HDA codec core
  ecb  ECB block cipher algorithm
  snd_pcm_oss  PCM OSS emulation for ALSA.
  snd_mixer_oss  Mixer OSS emulation for ALSA.
  iwl3945  Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
  iwlcore  iwl core
  snd_pcm  Midlevel PCM code for ALSA.
  pcmcia  PCMCIA Driver Services
  mac80211  IEEE 802.11 subsystem
  snd_seq_dummy  ALSA sequencer MIDI-through client
  snd_seq_oss  OSS-compatible sequencer module
  snd_seq_midi  Advanced Linux Sound Architecture sequencer MIDI synth.
  snd_rawmidi  Midlevel RawMidi code for ALSA.
  i915  Intel Graphics
  drm  DRM shared core routines
  i2c_algo_bit  I2C-Bus bit-banging algorithm
  sdhci_pci  Secure Digital Host Controller Interface PCI driver
  snd_seq_midi_event  MIDI byte <-> sequencer event coder
  sdhci  Secure Digital Host Controller Interface core driver
  snd_seq  Advanced Linux Sound Architecture sequencer.
  yenta_socket
  rsrc_nonstatic
  snd_timer  ALSA timer interface
  pcspkr  PC Speaker beeper driver
  video  ACPI Video Driver
  thinkpad_acpi  ThinkPad ACPI Extras
  pcmcia_core  Linux Kernel Card Services
  led_class  LED Class Interface
  cfg80211  wireless configuration support
  snd_seq_device  ALSA sequencer device management
  iTCO_wdt  Intel TCO WatchDog Timer Driver
  iTCO_vendor_support  Intel TCO Vendor Specific WatchDog Timer Driver Support
  output  Display Output Switcher Lowlevel Control Abstraction
  psmouse  PS/2 mouse driver
  btusb  Generic Bluetooth USB driver ver 0.5
  serio_raw  Raw serio driver
  nvram
  intel_agp
  agpgart  AGP GART driver
  snd  Advanced Linux Sound Architecture driver for soundcards.
  soundcore  Core sound module
  snd_page_alloc  Memory allocator for ALSA system.
  ohci1394  Driver for PCI OHCI IEEE-1394 controllers
  ieee1394
  e1000e  Intel(R) PRO/1000 Network Driver
  fbcon
  tileblit  Tile Blitting Operation
  font  Console Fonts
  bitblit  Bit Blitting Operation
  softcursor  Generic software cursor
  Boots
  Boots
  Languages
  Available Languages
  en_AU.utf8  English locale for Australia
  en_BW.utf8  English locale for Botswana
  en_CA.utf8  English locale for Canada
  en_DK.utf8  English locale for Denmark
  en_GB.utf8  English locale for Britain
  en_HK.utf8  English locale for Hong Kong
  en_IE.utf8  English locale for Ireland
  en_IN  English language locale for India
  en_NG  English locale for Nigeria
  en_NZ.utf8  English locale for New Zealand
  en_PH.utf8  English language locale for Philippines
  en_SG.utf8  English language locale for Singapore
  en_US.utf8  English locale for the USA
  en_ZA.utf8  English locale for South Africa
  Filesystems
  Mounted File Systems
  /dev/sda1  21.1 GiB total, 15.8 GiB free
  tmpfs  1.5 GiB total, 1.5 GiB free
  proc  0.0 B total, 0.0 B free
  sysfs  0.0 B total, 0.0 B free
  varrun  1.5 GiB total, 1.5 GiB free
  varlock  1.5 GiB total, 1.5 GiB free
  udev  1.5 GiB total, 1.5 GiB free
  tmpfs  1.5 GiB total, 1.5 GiB free
  devpts  0.0 B total, 0.0 B free
  fusectl  0.0 B total, 0.0 B free
  /dev/sda3  183.2 GiB total, 103.6 GiB free
  securityfs  0.0 B total, 0.0 B free
  binfmt_misc  0.0 B total, 0.0 B free
  gvfs-fuse-daemon  0.0 B total, 0.0 B free
  Shared Directories
  SAMBA
  NFS
  Display
  Display
  Resolution  1024x768 pixels
  Vendor  The X.Org Foundation
  Version  1.6.1.901
  Monitors
  Monitor 0  1024x768 pixels
  Extensions
  BIG-REQUESTS
  Composite
  DAMAGE
  DOUBLE-BUFFER
  DPMS
  DRI2
  GLX
  Generic Event Extension
  MIT-SCREEN-SAVER
  MIT-SHM
  RANDR
  RECORD
  RENDER
  SECURITY
  SGI-GLX
  SHAPE
  SYNC
  X-Resource
  XC-MISC
  XFIXES
  XFree86-DGA
  XFree86-DRI
  XFree86-VidModeExtension
  XINERAMA
  XInputExtension
  XKEYBOARD
  XTEST
  XVideo
  OpenGL
  Vendor  Tungsten Graphics, Inc
  Renderer  Mesa DRI Intel(R) 945GM GEM 20090418 2009Q1 x86/MMX/SSE2
  Version  1.4 Mesa 7.4.1
  Direct Rendering  Yes
  Network Interfaces
  Network Interfaces
  lo  Sent 59.42MiB, received 59.42MiB (127.0.0.1)
  eth0  Sent 0.00MiB, received 0.00MiB
  wmaster0  Sent 0.00MiB, received 0.00MiB
  wlan0  Sent 49.65MiB, received 1823.54MiB (192.168.0.2)
  pan0  Sent 0.00MiB, received 0.00MiB
  Users
  Human Users
  user  User
  System Users
  root  root
  daemon  daemon
  bin  bin
  sys  sys
  sync  sync
  games  games
  man  man
  lp  lp
  mail  mail
  news  news
  uucp  uucp
  proxy  proxy
  www-data  www-data
  backup  backup
  list  Mailing List Manager
  irc  ircd
  gnats  Gnats Bug-Reporting System (admin)
  nobody  nobody
  libuuid
  syslog
  klog
  hplip  HPLIP system user
  avahi-autoipd  Avahi autoip daemon
  saned
  messagebus
  avahi  Avahi mDNS daemon
  polkituser  PolicyKit
  haldaemon  Hardware abstraction layer
  pulse  PulseAudio daemon
  gdm  Gnome Display Manager
  mysql  MySQL Server
  Devices
  Processor
  Processors
  Intel(R) Core(TM) Duo CPU L2500 @ 1.83GHz  1833.00MHz
  Intel(R) Core(TM) Duo CPU L2500 @ 1.83GHz  1833.00MHz
  Memory
  Memory
  Total Memory  3088080 kB
  Free Memory  1172840 kB
  Buffers  47760 kB
  Cached  1412764 kB
  Cached Swap  2820 kB
  Active  364256 kB
  Inactive  1451148 kB
  Active(anon)  275240 kB
  Inactive(anon)  103620 kB
  Active(file)  89016 kB
  Inactive(file)  1347528 kB
  Unevictable  48 kB
  Mlocked  48 kB
  High Memory  2227016 kB
  Free High Memory  792552 kB
  Low Memory  861064 kB
  Free Low Memory  380288 kB
  Virtual Memory  4000176 kB
  Free Virtual Memory  3989216 kB
  Dirty  128 kB
  Writeback  0 kB
  AnonPages  352712 kB
  Mapped  108144 kB
  Slab  65556 kB
  SReclaimable  54316 kB
  SUnreclaim  11240 kB
  PageTables  7036 kB
  NFS_Unstable  0 kB
  Bounce  0 kB
  WritebackTmp  0 kB
  CommitLimit  5544216 kB
  Committed_AS  1190516 kB
  VmallocTotal  122880 kB
  VmallocUsed  9380 kB
  VmallocChunk  107892 kB
  HugePages_Total  0
  HugePages_Free  0
  HugePages_Rsvd  0
  HugePages_Surp  0
  Hugepagesize  4096 kB
  DirectMap4k  36856 kB
  DirectMap4M  872448 kB
  PCI Devices
  PCI Devices
  Host bridge  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub 
  VGA compatible controller  Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller 
  Display controller  Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller 
  Audio device  Intel Corporation 82801G 
  PCI bridge  Intel Corporation 82801G 
  PCI bridge  Intel Corporation 82801G 
  PCI bridge  Intel Corporation 82801G 
  PCI bridge  Intel Corporation 82801G 
  USB Controller  Intel Corporation 82801G 
  USB Controller  Intel Corporation 82801G 
  USB Controller  Intel Corporation 82801G 
  USB Controller  Intel Corporation 82801G 
  USB Controller  Intel Corporation 82801G 
  PCI bridge  Intel Corporation 82801 Mobile PCI Bridge 
  ISA bridge  Intel Corporation 82801GBM 
  IDE interface  Intel Corporation 82801G 
  SATA controller  Intel Corporation 82801GBM/GHM 
  SMBus  Intel Corporation 82801G 
  Ethernet controller  Intel Corporation 82573L Gigabit Ethernet Controller
  Network controller  Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection 
  CardBus bridge  Ricoh Co Ltd RL5c476 II 
  FireWire (IEEE 1394)  Ricoh Co Ltd R5C552 IEEE 1394 Controller 
  SD Host controller  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter 
  USB Devices
  Printers
  Printers
  No printers found
  Battery
  Battery: BAT0
  State  charging (load: 5650 mW)
  Capacity  45510 mWh / 66240 mWh (68.70%)
  Battery Technology  rechargeable (LION)
  Model Number  42T5251
  Serial Number  796
  Sensors
  ACPI Thermal Zone
  THM1  68°C
  THM0  65°C
  Input Devices
  Input Devices
   Power Button
   Lid Switch
   Sleep Button
   Macintosh mouse button emulation
   AT Translated Set 2 keyboard
   PC Speaker
   Video Bus
   ThinkPad Extra Buttons
   TPPS/2 IBM TrackPoint
   HDA Digital PCBeep
  Storage
  IDE Disks
  SCSI Disks
  ATA WDC WD2500BEVS-0
  Benchmarks
  CPU ZLib
  CPU ZLib
  This Machine  14932.579
  PowerPC 740/750 (280.00MHz)  2150.597408
  Intel(R) Celeron(R) M processor 1.50GHz  8761.604561
  CPU Fibonacci
  CPU Fibonacci
  This Machine  5.562
  Intel(R) Celeron(R) M processor 1.50GHz  8.1375674
  PowerPC 740/750 (280.00MHz)  58.07682
  CPU MD5
  CPU MD5
  This Machine  53.113
  PowerPC 740/750 (280.00MHz)  7.115258
  Intel(R) Celeron(R) M processor 1.50GHz  38.6607998
  CPU SHA1
  CPU SHA1
  This Machine  66.971
  PowerPC 740/750 (280.00MHz)  6.761451
  Intel(R) Celeron(R) M processor 1.50GHz  49.6752776
  CPU Blowfish
  CPU Blowfish
  This Machine  18.472
  Intel(R) Celeron(R) M processor 1.50GHz  26.1876862
  PowerPC 740/750 (280.00MHz)  172.816713
  FPU Raytracing
  FPU Raytracing
  This Machine  24.941
  Intel(R) Celeron(R) M processor 1.50GHz  40.8816714
  PowerPC 740/750 (280.00MHz)  161.312647

```

---

### Post by fifth on 2009-06-01
I should add the 3x350mb terminal test was copying to a usb drive. 

However all other problems are experienced on the hd partitions. ie deleting an empty directory from commandline happens instantly, but from kde/dolphin to the sys tray notification takes many minutes.

---

### Post by ranch hand on 2009-06-01
Thank you for that.  Just lurking and found an app new to me.

---

### Post by Wiebelhaus on 2009-06-01
SO then your only having this issue with solid state memory?

---

### Post by meborc on 2009-06-01
is it usb 2 or usb 1 device?

---

### Post by fifth on 2009-06-01
> **Wiebelhaus said:**
> SO then your only having this issue with solid state memory?

tbh difficult to say. I repeated the copy test  on just the hd, from the commandline without problems, it was fast.

But, copy actions, hd or usb, from KDE give the same original very slow results. Its to the point were I actively avoid pressing the delete key within Dolphin and use the terminal for all copy actions.

However, tonight, although to usb, the terminal copy was still showing the same very slow resuts, and system monitor shows cp as "Disk Sleep".

---

### Post by yelo3 on 2009-06-01
This also happens to my USB key... I thought it was a gvfs issue but since you told it also happens from the terminal. should we file a bug to linux?

when you copy from nautilus you see that the bar reaches the end almost in 10 seconds, then it stays to 100% for 1 minute)

---

### Post by fifth on 2009-06-01
> **yelo3 said:**
> This also happens to my USB key... I thought it was a gvfs issue but since you told it also happens from the terminal. should we file a bug to linux?

For me not just USB, I'm going to install Gnome and try the same hd based tests there. At the moment, I'm really not sure where the problem lies, i really need to do more tests.

---

### Post by LowSky on 2009-06-01
this happens to me transfering to usb, this is a linux wide issue, not just ubuntu. just a simple google search brings back plenty of people with USB issues.

I find it odd when Windows can transer a file just fine in a matter of seconds, yet my linux machine will take minutes or even stall out.

---

### Post by fifth on 2009-06-01
> **LowSky said:**
> this happens to me transfering to usb, this is a linux wide issue, not just ubuntu. just a simple google search brings back plenty of people with USB issues.

I find it odd when Windows can transer a file just fine in a matter of seconds, yet my linux machine will take minutes or even stall out.

Only thing is i didnt have these problems before Karmic, i've not googled but i think 20-30 minutes to transfer 350mb even on any distro i'd guess is above the norm.

And as i've mentioned, the problems are not just to usb, also within Dolphin hd to hd with 0b files to trash takes a long time.

I think i could be experiencing more than one issue, kde problems and/or usb problems.

Going to test all options thoroughly tomorrow.

---

### Post by ranch hand on 2009-06-02
I have been just lurking out of interest.

I assume you are talking about thumb drives on your USB.  I run 3 HDDs on USB and really don't have any problem with large files (in the 1 - 1.5 GB range) to and from my internals under any Ubuntu I have on here, including Kinky Kitty (9.10).

This is primarily a Gnome box but I have a couple Kubuntus and a Mandriva2009-1-KDE.

All tranfers are run from gnome though because I like nautilus.

---

### Post by fifth on 2009-06-02
I've ran the same tests under Gnome with good results.

HD transfers were about 21Mb/s and USB were roughly 19Mb/s. The tests were run from a terminal window and from Nautilus with good results on both. The only pause I saw in the copying was under the GUI where it paused momentarily between files as a thumbnail was generated in Nautilus, but nothing severe.

It appears the problem is with KDE. I've tried disabling effects etc to check for improvements but nothing seems to help. From what I observe, when the copy action is listed in the notification tray, its seems to loose all priority and takes an age to complete. Although I can't figure why the same poor performance should be seen when copying from the commandline in Konsole.

> **ranch hand said:**
> 
I assume you are talking about thumb drives on your USB.  I run 3 HDDs on USB and really don't have any problem with large files (in the 1 - 1.5 GB range) to and from my internals under any Ubuntu I have on here, including Kinky Kitty (9.10).

Yep, USB flash drives. I tried with an 8gb JetFlash and a 32gb Kingston, same results on both.

---

### Post by ranch hand on 2009-06-02
I won't comment further as I am one of those folks who is not compatible with KDE.

Happy it works with Gnome.

---

### Post by ronacc on 2009-06-02
I have run into large speed variences with sd cards on my eeepc , cards of the same size and class can yeild radicly different results and even the same card seems to perfom differently some times , I have had cases where a 30 to 50 MB update would take 2 hrs to finish (the d/l went fast it was the unpack/install that drug out ) and this is with 2GB of ram .This is with jaunty release installed on the SD card.

---

### Post by crjackson on 2009-06-02
I have VERY slow USB transfers to any device. Grabbing a few pictures from my camera takes several minutes, whereas the same transfer with windows takes place in seconds.

Even my printer takes ages to receive a large buffer of data. What should take seconds (and does in windows) takes SEVERAL minutes in Ubuntu.

I sure would like to see this situation improve. It's kind of embarrassing at times when being jabbed/jibbed by avid windows users.

---

### Post by CyberAngel on 2009-06-14
Same problem for me using kde :(

---

### Post by alphacrucis2 on 2009-06-14
I'm a gnome user. Tested copy from ext4 to to various USB flash devices. Getting an average write transfer rate of about 20 megabytes per second. Going the other way flash to EXT4 I am getting 35 megabytes per second. All of which seems pretty reasonable. This is using Nautilus to do the copy. Does the problem occur only with KDE then?

---

### Post by ranch hand on 2009-06-14
I have installed 9.10A2 on a dual SATA drive.  A1 is on an internal.

The external will boot from only the first HDD (no raid, don't like it) so I install / on it and /home on the other.

Transfered 2.9Gb from sdb6 to sdb7 at 20Mb/sec.  Now I have tunes.

---

### Post by fifth on 2009-06-14
> **alphacrucis2 said:**
> Does the problem occur only with KDE then?

Yeah just KDE, although I can fire-up Nautilus on KDE and the file copies in Nautilus are fine. Just when trying the same thing from Dolphin grinds to a halt, pressing delete on a 0 byte file takes 3/4 minutes to move to trash.

---

### Post by ranch hand on 2009-06-14
WOW

My transfer speeds are faster usually than what I posted above.  If I go from an external to an internal, or the other way, or internal/internal it usually runs about 25 to 34Mb/sec.  Having to go both ways through the usb interface slows it down some.

For me to do anything and enjoy it on KDE I have to install a bunch of Gnome stuff and I don't, for me, see the point.  KDE and I just don't get along.  I don't like Dolphin or Konquerer or Krusader, they just don't access other drives well.  I don't like the package management either.

Probably a personality fault.

---

### Post by fifth on 2009-06-14
> **ranch hand said:**
> WOW

My transfer speeds are faster usually than what I posted above.  If I go from an external to an internal, or the other way, or internal/internal it usually runs about 25 to 34Mb/sec.  Having to go both ways through the usb interface slows it down some.

For me to do anything and enjoy it on KDE I have to install a bunch of Gnome stuff and I don't, for me, see the point.  KDE and I just don't get along.  I don't like Dolphin or Konquerer or Krusader, they just don't access other drives well.  I don't like the package management either.

Probably a personality fault.

Well *normally* I would get about 21Mb/s on the sata hd and about 19Mb/s to usb flash drive. This problem only started with the transition to KDE 4.3 so I assume its a problem that will be fixed soon :D, then I'll be able to stop loading up the retro Nautilus file manager ;)

---

### Post by ranch hand on 2009-06-14
Yup.  It is a pain to use KDE stuff on Gnome and the other way too.  You have to load too many dependancies.

Probably not a real problem to many folks seeing the size of HDDs now but I try to keep my root partition less than 50% full and about 10Gb.  You start installing the libs for the other desktop and you start using some serious room.

But we do have that option and it is handy at times.

---

### Post by nhasian on 2009-06-15
i dont know if it makes a difference between kde/gnome as you guys were discussing, but I've been able to duplicate the issue with my fresh installation of Ubuntu Karmic Koala 64bit Alpha2.

while copying data to my 16G Corsair USB flashdrive, the transfer rate slows to a crawl - 800k/s  it took 15 minutes to transfer 1 gig.

I dont know if anyone else is experiencing this other issue as well but i cant even get a usb drive (either flash or standard) to mount at first since it tries to mount it as a cd media at /media/cdrom0 and tries to use the wrong filesystem.  It only happens to the first usb drive, then plugging in any additional usb drives work fine.

I even have an external usb hard disk with multiple partitions.  the first partition fails to mount at /media/cdrom0 then the remaining partitions mount fine.

---

### Post by Hated On Mostly on 2009-06-15
> **LowSky said:**
> this happens to me transfering to usb, this is a linux wide issue, not just ubuntu. just a simple google search brings back plenty of people with USB issues.

I find it odd when Windows can transer a file just fine in a matter of seconds, yet my linux machine will take minutes or even stall out.

Yes.

Check out this long thread:

[http://ubuntuforums.org/showthread.php?t=793688](http://ubuntuforums.org/showthread.php?t=793688)

or this bug report

[https://bugs.launchpad.net/linux/+bug/88746?comments=all](https://bugs.launchpad.net/linux/+bug/88746?comments=all)

There are a bunch of links in the thread (and can be found through google) to bug reports on other distributions and the kernel going back several years. Linux has a problem with USB 2.0 transfers and nobody seems to be looking at it.

The current workarounds (unacceptable as the problem should be fixed) include getting a PCI(e) USB card with a chipset that doesn't show that problem or using a powered USB hub.

Tons of bug reports filed, tons of logs provided, at least 2 recent offers allowing developers remote access to machines with the problem, but complete silence from ubuntu developers, linux kernel developers, etc.

---

### Post by Regenweald on 2009-06-16
I also think it's with Linux in general, and it depends on the hardware. On a great day I might get around 14mb transfer speeds,but even that usually goes down to between 9 and 7mb. I'm currently getting a whopping 4mb/s transferring some avi's to a flash drive. My transfer speeds have been this way since 8.04
I think i'l dig further into it.

Now usb3.0 is around the corner. i wonder if things will get better.

---

### Post by lazka on 2009-06-17
You are lucky.. I get 2 MB/s to an external harddrive... and 100% IO Wait.. and everything starts to lag....

---

### Post by fifth on 2009-06-17
Seems most of the slow downs everyone else is experiencing are quite different from mine :(

The slow downs I see are _not_ USB related. The slow figures I've given since my opening post are all on the hd and happens only with KDE apps, ie with Plasma Desktop, Konsole and Dolphin.

If I launch a Gnome app (ie Nautilus), or just switch to Gnome, the problem goes away instantly. I now rely on Nautilus when I'm running KDE to do all my file management :(

---

### Post by ranch hand on 2009-06-17
Nautilus is easier to do it in too.

---

### Post by fifth on 2009-06-18
> **ranch hand said:**
> Nautilus is easier to do it in too.

Got to admit that some things are, its much more responsive for one. But it just doesn't fit in with KDE and I really miss split views for easy drag/drop,compare,etc - although I think I've read that split views in Nautilus is being tested for release.

---

### Post by ranch hand on 2009-06-18
I will admit to pulling Nautilus up twice on occasion, side by side in the same window, for that very reason.  I have to thank Windows Explorer for that bit of knowledge.

It seemed like some file or other was always getting corrupted and had to be replace from the install disk.  I wanted to be able to check the buggers and make sure they really matched (as much as you can on that crappy OS) so that is how I did it.  Works better in Nautilus.

---

### Post by taavikko on 2009-06-20
Anyone noticed that trasnfering files in KDE brings system to a crawl?

Or is it just me (once again)?

from "sda5 -> sdb1" both of them are SataII,
transferred roughly 130GB to safety... During this operation system was a near crawling state, speeds were ranging from
10MB/s -> 90MB/s

---

### Post by fifth on 2009-06-20
A quick video will show the problem I'm having ...

[http://www.flickr.com/photos/47494436@N00/3644487124](http://www.flickr.com/photos/47494436@N00/3644487124)

An empty text file is created and sent to the trash.

---

### Post by fifth on 2009-06-27
Just tested this with a new user without any problems. Looks  like it is something in my config/settings. Time to hunt it down ...

---

### Post by fifth on 2009-06-27
> **fifth said:**
> Just tested this with a new user without any problems. Looks  like it is something in my config/settings. Time to hunt it down ...

Finding the offending setting was a bit tedious, so I removed the .kde directory and the problems solved.

Would have been nice to know what was causing it though.

---

### Post by n3had on 2009-08-10
> **crjackson said:**
> I have VERY slow USB transfers to any device. Grabbing a few pictures from my camera takes several minutes, whereas the same transfer with windows takes place in seconds.

Even my printer takes ages to receive a large buffer of data. What should take seconds (and does in windows) takes SEVERAL minutes in Ubuntu.

I sure would like to see this situation improve. **It's kind of embarrassing at times when being jabbed/jibbed by avid windows users.**

I was totally put to shame just now... My friend needed something to copy to his 8gb flash drive and it took ages to complete and he was like IS THIS THE REASON YOU USE LINUX FOR? I just couldn't reply and then we had windoze/linux arguments. SO anyways. Iam having AMD x2 4200+ and ASUS M2N-VM DH. So is this AMD/ASUS specific? or a major issue effecting everybody? and any fixes yet? 

thankyou
nehad

---

### Post by scaine on 2009-08-10
When you plug in the USB device, do a quick "dmesg" in a terminal and see if it's throwing up any errors about being unable to drive the device at full power.

I hate that Linux silently writes really important stuff to dmesg.  Are there any good apps to pop up windows/notifications regarding dmesg stuff?  Is there a log file that dmesg generates?  Not everything in dmesg appears in /var/log/messages that I can tell...

---

### Post by Arup on 2009-08-10
Try turning off USB Legacy support in BIOS and turn on AHCI and see if it improves.

---

