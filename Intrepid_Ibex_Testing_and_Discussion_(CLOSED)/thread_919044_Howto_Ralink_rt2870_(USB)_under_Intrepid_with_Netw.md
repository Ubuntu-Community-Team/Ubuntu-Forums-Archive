---
title: "Howto: Ralink rt2870 (USB) under Intrepid with Networkmanager"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RaZoR1394 on 2008-09-13
Howto is now posted on PBwiki to allow collaboration and observe changes.

[http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

---

### Post by RaZoR1394 on 2008-09-14
I have tested this guide after editing some parts of it and it works fine on another computer with a newly install rt2870 device. Sorry for the typos and the misses in the previous version.

It seems that parts of build-essential are already installed but I'm not entirely sure.

I hope someone here could help with a way to get ra0 up before NetworkManager starts in a clean way.

---

### Post by Absurd on 2008-09-15
> **RaZoR1394 said:**
> 
```
wget http://launchpadlibrarian.net/17325896/RT2870-v1.3.1.0-2.6.27.patch

```


hi

I don't use ubuntu anymore, but I do have a device with rt2870 and I'm curious

what exactly does this patch make the driver do? (with the exception of enabling the built-in WPA support)

so far, my only problem with this driver is the Bulk In Failed messages (dmesg)

---

### Post by RaZoR1394 on 2008-09-16
> **Absurd said:**
> hi

I don't use ubuntu anymore, but I do have a device with rt2870 and I'm curious

what exactly does this patch make the driver do? (with the exception of enabling the built-in WPA support)

so far, my only problem with this driver is the Bulk In Failed messages (dmesg)

As far as I know and as I wrote it enables the driver to be compiled with Linux version 2.6.27. I'm not entirely sure but I think It's needed for .25 and .26 as well. I'm not sure of what EXACTLY it does in terms of kernel features. I'll let someone with more kernel knowledge answer that.

You mean this:

> 
[ 3385.574332] Bulk In Failed. Status=-71, BIIdx=0x5, BIRIdx=0x5, actual_length= 0x0


---

### Post by Absurd on 2008-09-16
yeah, that; I don't have a problem with those messages themselves, but I noticed that they usually seem to lead to "CMDTHREAD_RESET_BULK_IN" which causes the module to remove itself from memory (e.g. modprobe -r rt2870sta).

As for the kernel compilation, I guess that's understood if it won't compile with newer kernels. I remember when I couldn't get the driver to compile under 2.6.24 and I emailed ralink (and they sent me fixed code).

---

### Post by Jackie999 on 2008-09-17
Thanks for the howto ..I went thru step by step and all went well..but after reboot still have no connection:
```
jackie@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

Any suggestions?

---

### Post by Absurd on 2008-09-17
what happens when you insert the module? (sudo modprobe rt2870sta)

did you try different usb ports?

---

### Post by RaZoR1394 on 2008-09-18
> **Jackie999 said:**
> Thanks for the howto ..I went thru step by step and all went well..but after reboot still have no connection:
```
jackie@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

Any suggestions?

Please check that ndiswrapper is not loaded during startup and that any Windows driver is not installed. To list current installed Windows drivers use

```

ndiswrapper -l

```

and to remove the Windows driver

```

sudo ndiswrapper -r *Your driver here*

```

 If ndiswrapper is listed in /etc/modules uncomment it like I have done. You can blacklist the module in this file as well, /etc/modprobe.d/blacklist .

Please post the output of

```

dmesg

```

and

```

lsmod

```

I hope this will shed some light on the problem. Are you possibly using the amd64 edition? I have only tested this on i386 so far.

---

### Post by Jackie999 on 2008-09-18
> what happens when you insert the module? (sudo modprobe rt2870sta)Nothing appears to have happened ..although in dmesg I see that the driver is loaded..but no device shows up in iwconfig.

> did you try different usb ports?     Yes, I've tried both of them - they're only 1.1 - but I'm pretty sure that doesn't matter.

> Please check that ndiswrapper is not loaded during startup and that any Windows driver is not installedI removed the windows driver that I loaded, and completely removed the ndiswrapper with synaptic before I began. Other times I did a format/reinstall without installing ndiswrapper to be sure it wasn't leaving stuff behind that would hinder install of the rt2870.

> Are you possibly using the amd64 edition?No, this is a rather old Toshiba Satellite notebook.  It won't load the native driver..and the ndiswrapper, when I break down and install it, freezes something terrible. I wonder if the problems are related...

Thanks for the suggestions.

---

### Post by RaZoR1394 on 2008-09-18
> **Jackie999 said:**
> Nothing appears to have happened ..although in dmesg I see that the driver is loaded..but no device shows up in iwconfig.

Yes, I've tried both of them - they're only 1.1 - but I'm pretty sure that doesn't matter.

I removed the windows driver that I loaded, and completely removed the ndiswrapper with synaptic before I began. Other times I did a format/reinstall without installing ndiswrapper to be sure it wasn't leaving stuff behind that would hinder install of the rt2870.

No, this is a rather old Toshiba Satellite notebook.  It won't load the native driver..and the ndiswrapper, when I break down and install it, freezes something terrible. I wonder if the problems are related...

Thanks for the suggestions.

On my Engenius package they mention USB 1.1 in the form factor field but not if it works with it. I think it could work but the problem is that USB 1.1 is limited to 12Mbit/s in theory. The real speed could be worse. I'm just saying this incase you get it working. Currently I only get about 3MB/s+ from my N router.

This page over at the r2x00 forums indicates it may work but according to the datasheet only 2.0 is mentioned.

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?t=4200](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?t=4200)

As I wrote earlier could you post your dmesg and lsmod output?

---

### Post by Jackie999 on 2008-09-18
> As I wrote earlier could you post your dmesg and lsmod output?     Yes I most certainly will..I've printed your post and will post back as soon as I'm home. For now (since I'm at work) I'll make do with reading that serialmonkey thread you've posted.
Thanks again.

---

### Post by Jackie999 on 2008-09-18
Here are the last lines of the dmesg on a fresh bootup:
```
[   43.908548] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   43.911086] cs: IO port probe 0x3e0-0x4ff: clean.
[   43.912357] cs: IO port probe 0x820-0x8ff: clean.
[   43.913317] cs: IO port probe 0xc00-0xcf7: clean.
[   43.914606] cs: IO port probe 0xa00-0xaff: clean.
[   43.916381] cs: IO port probe 0x820-0x8ff: clean.
[   43.917361] cs: IO port probe 0xc00-0xcf7: clean.
[   43.918664] cs: IO port probe 0xa00-0xaff: clean.
[   46.542528] loop: module loaded
[   46.610778] lp0: using parport0 (interrupt-driven).
[   47.329872] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
[   48.110872] EXT3 FS on sda1, internal journal
[   50.377409] type=1505 audit(1221778327.216:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3806
[   51.012552] type=1505 audit(1221778327.852:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3812
[   51.014076] type=1505 audit(1221778327.852:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3812
[   51.417530] ip_tables: (C) 2000-2006 Netfilter Core Team
[   55.510409] ACPI: WMI: Mapper loaded
[   61.771891] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   62.175243] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   62.175278] apm: overridden by ACPI.
[   62.858356] ppdev: user-space parallel port driver
[   71.430664] Bluetooth: Core ver 2.13
[   71.439762] NET: Registered protocol family 31
[   71.439791] Bluetooth: HCI device and connection manager initialized
[   71.439811] Bluetooth: HCI socket layer initialized
[   71.586056] Bluetooth: L2CAP ver 2.11
[   71.586087] Bluetooth: L2CAP socket layer initialized
[   71.883337] Bluetooth: RFCOMM socket layer initialized
[   71.884550] Bluetooth: RFCOMM TTY layer initialized
[   71.884595] Bluetooth: RFCOMM ver 1.10
[  107.715978] NET: Registered protocol family 10
[  107.724627] lo: Disabled Privacy Extensions
[  107.729163] ADDRCONF(NETDEV_UP): eth0: link is not ready

```and here is the lsmod:
```
jackie@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
rfcomm                 44432  2 
l2cap                  30464  9 rfcomm
bluetooth              61924  4 rfcomm,l2cap
ppdev                  15620  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
wmi                    14504  0 
pci_slot               12552  0 
sbs                    19464  0 
container              11520  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
loop                   23180  0 
joydev                 18368  0 
snd_ali5451            27532  3 
snd_ac97_codec        111652  1 snd_ali5451
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
video                  25104  0 
pcmcia                 43052  0 
output                 11008  1 video
snd_pcm                83204  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
ndiswrapper           196380  0 
parport_pc             39204  1 
snd_seq_dummy          10884  0 
parport                42604  3 ppdev,lp,parport_pc
psmouse                45200  0 
serio_raw              13444  0 
battery                18436  0 
snd_seq_oss            38528  0 
ac                     12292  0 
snd_seq_midi           14336  0 
button                 14224  0 
snd_rawmidi            29952  1 snd_seq_midi
i2c_ali1535            14340  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_ali15x3            14852  0 
yenta_socket           31756  2 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         19072  1 yenta_socket
i2c_core               31892  2 i2c_ali1535,i2c_ali15x3
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    63140  16 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ali_agp                13696  1 
soundcore              15328  1 snd
snd_page_alloc         16136  1 snd_pcm
agpgart                42184  1 ali_agp
evdev                  17696  10 
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sg                     39732  0 
sr_mod                 22340  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
pata_ali               16516  2 
pata_acpi              12160  0 
libata                177440  3 ata_generic,pata_ali,pata_acpi
e100                   41484  0 
mii                    13440  1 e100
scsi_mod              155212  4 sg,sr_mod,sd_mod,libata
dock                   16656  1 libata
ohci_hcd               31888  0 
usbcore               148848  3 ndiswrapper,ohci_hcd
thermal                23708  0 
processor              43052  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
uvesafb                34788  0 
cn                     15776  1 uvesafb
fuse                   60828  3 

```Here is the ndiswrapper -1 and trying to get the ra0 up:
```
jackie@ubuntu:~$ ndiswrapper -1
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
jackie@ubuntu:~$ sudo modprobe rt2870sta
[sudo] password for jackie: 
jackie@ubuntu:~$ 
```And finally the new lines in the dmesg after the 'sudo modprobe rt2870sta up :
```
[  107.715978] NET: Registered protocol family 10
[  107.724627] lo: Disabled Privacy Extensions
[  107.729163] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  198.768970] ppdev0: registered pardevice
[  198.820592] ppdev0: unregistered pardevice
[  200.915324] ppdev0: registered pardevice
[  200.965510] ppdev0: unregistered pardevice
[  201.428570] ppdev0: registered pardevice
[  201.480164] ppdev0: unregistered pardevice
[  393.282675] rtusb init --->
[  393.289581] usbcore: registered new interface driver rt2870
jackie@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jackie@ubuntu:~$ lsusb
Bus 001 Device 002: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jackie@ubuntu:~$ 

```Any suggestions you can make I'd gladly try ..I don't know what I'm doing wrong..I'll format again if necessary. I've been trying to get it going on Gutsy then Hardy and now updating to Ibex....all the time formatting and starting fresh each time.

I realize I won't get the benefit of the 'n' ..but anything it better than wired

---

### Post by RaZoR1394 on 2008-09-18
Doesn't seem like rt2870sta is loaded on bootup.

Try this after bootup

```

sudo modprobe rt2870
sudo ifconfig ra0 inet up
sudo /etc/init.d/NetworkManager restart

```

Please post your /etc/modules as well.

---

### Post by Jackie999 on 2008-09-18
Still no luck:
```
jackie@ubuntu:~$ sudo modprobe rt2870
FATAL: Module rt2870 not found.
jackie@ubuntu:~$ sudo modprobe rt2870sta
jackie@ubuntu:~$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device
jackie@ubuntu:~$ sudo /etc/init.d/NetworkManager restart
Restarting Network connection manager daemon: NetworkManager.
jackie@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jackie@ubuntu:~$ 


```Here is my /etc/modules :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
```I also had the following line in it yesterday, after following your how to, but when it wasn't working I put back to default:

```
alias ra0 rt2870sta                      
```

---

### Post by Absurd on 2008-09-18
> Bus 001 Device 002: ID 050d:815c Belkin Components 

According to the source code, your device is not supported by this driver.The only Belkin device that's supported is shown as

```
 {USB_DEVICE(0x050D,0x8053)}, /* Belkin */
```

The file is include/rt2870.h

are you sure that your device uses rt2870? if so, all that the author of the patch might have to do is add the following to the header

```
{USB_DEVICE(0x050D,0x815C)}, /* Belkin */
```

That just might work.

---

### Post by Jackie999 on 2008-09-19
EUREKA!!! It works :):):)
I'm so happy..thank you both very much ...you have no idea how many hours I've been messing with this.
It's a bit of fooling around to get it up ...but I'm writing this with it (with WPA). Now I have a device to work with I can play with settings to get it automatic.
I did as Absurd suggested and replaced the '8053' with my '815C' in the /include/rt2870.h
Thanks again :)

---

### Post by Absurd on 2008-09-19
you're welcome

all you had to do was add the line; no need to replace

---

### Post by aextance on 2008-09-27
I think I'm in a similar situation to Jackie999, having a USB 1.1 port that I'm trying to get running with an RT2870 adaptor. 

Unfortunately, I can't even get beyond "make"-ing the driver. When I try, what I get is as follows:

andy@andyslaptop:~/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0$ sudo make
[sudo] password for andy: 
make -C tools
make[1]: Entering directory `/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools'
/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-19-386/build SUBDIRS=/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/os/linux modules
make: *** /lib/modules/2.6.24-19-386/build: No such file or directory. Stop.
make: *** [LINUX] Error 2

I'm not actually using Intrepid - I've just recently installed Hardy and am still ironing out a few glitches. 

I thought the error might be to do with build-essential, but I have checked and I have the most current version.

Any ideas?

---

### Post by RaZoR1394 on 2008-09-27
> **aextance said:**
> I think I'm in a similar situation to Jackie999, having a USB 1.1 port that I'm trying to get running with an RT2870 adaptor. 

Unfortunately, I can't even get beyond "make"-ing the driver. When I try, what I get is as follows:

andy@andyslaptop:~/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0$ sudo make
[sudo] password for andy: 
make -C tools
make[1]: Entering directory `/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools'
/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-19-386/build SUBDIRS=/home/andy/rt2870/2008_0718_RT2870_Linux_STA_v1.3.1.0/os/linux modules
make: *** /lib/modules/2.6.24-19-386/build: No such file or directory. Stop.
make: *** [LINUX] Error 2

I'm not actually using Intrepid - I've just recently installed Hardy and am still ironing out a few glitches. 

I thought the error might be to do with build-essential, but I have checked and I have the most current version.

Any ideas?

Jackie:s problem seemed to be because of a missing id in the driver. USB 1.1 was not the problem however it will limit the speed significantly. Usually the error you've gotten happens due to missing kernel sources. What I can think of is that you are missing any of these packages:

linux-headers
linux-source
linux-restricted-modules

My guess is that It's the first one as I don't have the second one and I've seen that the third one gets installed during each kernel update.

---

### Post by aextance on 2008-09-28
OK, I found the build file - turns out the make file has the following line in it:

/lib/modules/$(shell uname -r)/build

which points the make process to /lib/modules/2.6.24-19-386/build on my system, when the build symbolic link is actually at /lib/modules/2.6.24-19-generic/build.

So having done everything else you mention - except install the patch as I'm not in Intrepid - I think I'm still struggling. 

When do a sudo modprobe I get the following worrying message:
FATAL: Error inserting rt2870sta (/lib/modules/2.6.24-19-386/kernel/drivers/net/wireless/rt2870sta.ko): Invalid module format

When I do an lsusb it definitely comes back saying that it's an RT2870 device, so I don't get it. Unless it's because I'm following this procedure for Intrepid, but I'm not using the patch, so it should go OK, shouldn't it ?

I'm gonna recheck the other threads on using the RT2870 driver in case I've missed something...

---

### Post by RaZoR1394 on 2008-09-28
> **aextance said:**
> OK, I found the build file - turns out the make file has the following line in it:

/lib/modules/$(shell uname -r)/build

which points the make process to /lib/modules/2.6.24-19-386/build on my system, when the build symbolic link is actually at /lib/modules/2.6.24-19-generic/build.

So having done everything else you mention - except install the patch as I'm not in Intrepid - I think I'm still struggling. 

When do a sudo modprobe I get the following worrying message:
FATAL: Error inserting rt2870sta (/lib/modules/2.6.24-19-386/kernel/drivers/net/wireless/rt2870sta.ko): Invalid module format

When I do an lsusb it definitely comes back saying that it's an RT2870 device, so I don't get it. Unless it's because I'm following this procedure for Intrepid, but I'm not using the patch, so it should go OK, shouldn't it ?

I'm gonna recheck the other threads on using the RT2870 driver in case I've missed something...

There is a guide for Hardy and 2.6.24 which involves a special patch made for that kernel. Search for rt2870 on this forum and you'll find it. This guide was tested on Intrepid and not on Hardy.

---

### Post by Jackie999 on 2008-09-29
While this did work for me for a few days (although wouldn't stay connected for more than 10~15 minutes) now, when I try ifconfig ra0 up I'm getting the following error. I've tried rebuilding and no change.

```
[ 1212.583058] <-- RTMPAllocAdapterBlock, Status=0
[ 1212.596485] usbcore: registered new interface driver rt2870
[ 1242.807814] ifconfig: page allocation failure. order:6, mode:0x0
[ 1242.807863] Pid: 7867, comm: ifconfig Tainted: P          2.6.27-4-generic #1
[ 1242.807876]  [<c03924c6>] ? printk+0x1d/0x1f
[ 1242.807919]  [<c018baf7>] __alloc_pages_internal+0x387/0x490
[ 1242.807949]  [<c01081ba>] dma_alloc_pages+0x2a/0x30
[ 1242.807983]  [<c010828e>] dma_alloc_coherent+0xce/0x280
[ 1242.808216]  [<cf8c47a9>] hcd_buffer_alloc+0x49/0x90 [usbcore]
[ 1242.808416]  [<cf8b843a>] usb_buffer_alloc+0x2a/0x30 [usbcore]
[ 1242.808446]  [<cfdb6fa7>] NICInitTransmit+0xc7/0x9c0 [rt2870sta]
[ 1242.808666]  [<cfdb7966>] RTMPAllocTxRxRingMemory+0xc6/0x150 [rt2870sta]
[ 1242.808695]  [<c010529f>] ? mcount_call+0x5/0x16
[ 1242.808725]  [<cfda56b0>] rt28xx_open+0xd0/0x590 [rt2870sta]
[ 1242.808765]  [<c030adfa>] dev_open+0xaa/0xe0
[ 1242.808799]  [<c0394926>] ? _spin_unlock_bh+0x16/0x20
[ 1242.808825]  [<c030a21f>] ? dev_set_rx_mode+0x2f/0x40
[ 1242.808834]  [<c030a4a9>] dev_change_flags+0x149/0x1d0
[ 1242.808843]  [<c03568b2>] devinet_ioctl+0x4f2/0x550
[ 1242.808862]  [<c030aaad>] ? dev_ioctl+0x27d/0x520
[ 1242.808870]  [<c01be052>] ? path_walk+0xa2/0xb0
[ 1242.808892]  [<c035755a>] inet_ioctl+0x9a/0xc0
[ 1242.808901]  [<c02fb1b8>] sock_ioctl+0x68/0x250
[ 1242.808924]  [<c01cad60>] ? alloc_fd+0xe0/0x100
[ 1242.808944]  [<c02fb150>] ? sock_ioctl+0x0/0x250
[ 1242.808952]  [<c01c048d>] vfs_ioctl+0x2d/0x90
[ 1242.808963]  [<c01c0676>] do_vfs_ioctl+0x66/0x1f0
[ 1242.808971]  [<c01c086b>] sys_ioctl+0x6b/0x70
[ 1242.808978]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[ 1242.808986]  [<c0390000>] ? native_cpu_up+0x56/0x180
[ 1242.808996]  =======================
[ 1242.809001] Mem-Info:
[ 1242.809008] DMA per-cpu:
[ 1242.809015] CPU    0: hi:    0, btch:   1 usd:   0
[ 1242.809020] Normal per-cpu:
[ 1242.809024] CPU    0: hi:   90, btch:  15 usd:  87
[ 1242.809034] Active:31258 inactive:19942 dirty:9 writeback:0 unstable:0
[ 1242.809037]  free:1041 slab:3640 mapped:6194 pagetables:501 bounce:0
[ 1242.809047] DMA free:1168kB min:128kB low:160kB high:192kB active:4352kB inactive:5088kB present:15852kB pages_scanned:0 all_unreclaimable? no
[ 1242.809054] lowmem_reserve[]: 0 221 221 221
[ 1242.809066] Normal free:2996kB min:1840kB low:2300kB high:2760kB active:120680kB inactive:74680kB present:227296kB pages_scanned:0 all_unreclaimable? no
[ 1242.809073] lowmem_reserve[]: 0 0 0 0
[ 1242.809080] DMA: 34*4kB 1*8kB 2*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1168kB
[ 1242.809101] Normal: 71*4kB 189*8kB 35*16kB 8*32kB 2*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2996kB
[ 1242.809120] 30994 total pagecache pages
[ 1242.809125] 1678 pages in swap cache
[ 1242.809131] Swap cache stats: add 20127, delete 18449, find 8578/8959
[ 1242.809136] Free swap  = 634816kB
[ 1242.809139] Total swap = 698788kB
[ 1242.827331] 61424 pages RAM
[ 1242.827343] 0 pages HighMem
[ 1242.827346] 1867 pages reserved
[ 1242.827349] 45957 pages shared
[ 1242.827353] 49075 pages non-shared
[ 1242.827365] <-- ERROR in Alloc TX TxContext[3] HTTX_BUFFER !! 
[ 1242.934347] <-- RTMPAllocTxRxRingMemory, Status=3
[ 1242.934403] ERROR!!! RTMPAllocDMAMemory failed, Status[=0x00000003]
[ 1242.934418] !!! RT2870 Initialized fail !!!

```

---

### Post by Jackie999 on 2008-10-01
I have it working again using the newest driver (version 1.4.0.0) from ralinktech:```
http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
```Since my device isn't in the /include/rt2870.h - I added it
```
lsusb
Bus 001 Device 002: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Then in /os/linux/ I changed the two lines (the n to y):
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```On boot I had to 
```
sudo modprobe rt2870sta
sudo ifconfig ra0 up
```It immediately asked for my wireless password ..then connected
```
iwconfig
ra0       RT2870 Wireless  ESSID:"Your Mom on four"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:6C:6C:6D   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-50 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm not sure if this now supports the 802.11n....
Thanks again to everyone who helped me getting it going

---

### Post by RaZoR1394 on 2008-10-01
Glad to hear that. Sorry I couldn't help lately cause I'm not really an expert on this.

I've put the guide on pbwiki so changes can be observed:

[http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

I had thoughts about putting it on wiki.ubuntu.com but my guess is that It's a lot stricter and I couldn't figure out how to post.

---

### Post by RaZoR1394 on 2008-10-01
I've been trying this new driver for some hours and wireless reception information seems to be more accurate.

---

### Post by Jackie999 on 2008-10-01
Yes...I thought the connection was more stable and of a better quality.
Do you know..it says in the release doc
> 16. Support Linux Kernel 2.6.27Would that mean it would work also for Hardy users that haven't stepped up to Intrepid yet?
I'm not sure about backwards compatiblity here....

---

### Post by RaZoR1394 on 2008-10-02
All I can gather from that line is that this driver should work better with 2.6.27.

This post indicates that the latest driver should work without any modifications with Hardy on 2.6.24.

[http://ubuntuforums.org/showpost.php?p=5891745&postcount=44](http://ubuntuforums.org/showpost.php?p=5891745&postcount=44)

---

### Post by funkz on 2008-10-09
> **Jackie999 said:**
> I have it working again using the newest driver (version 1.4.0.0) from ralinktech:```
http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
```Since my device isn't in the /include/rt2870.h - I added it
```
lsusb
Bus 001 Device 002: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Then in /os/linux/ I changed the two lines (the n to y):
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```On boot I had to 
```
sudo modprobe rt2870sta
sudo ifconfig ra0 up
```It immediately asked for my wireless password ..then connected
```
iwconfig
ra0       RT2870 Wireless  ESSID:"Your Mom on four"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:6C:6C:6D   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-50 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm not sure if this now supports the 802.11n....
Thanks again to everyone who helped me getting it going

Thank you, thank you, thank you! :D This worked a treat. Have been trying to get this going via the same driver you said but version 1.3, which was being all dodgy (not connecting, being wierd). Then I was trying a lot with ndiswrapper and it wouldn't load the drivers. Worked instantly with this driver. Now just need to add it to my /etc/modules...

I'm on Xubuntu 8.04 on amd64 with a Belking N Wireless USB F5D8053AU (aka F5D8053 in non-Australia).

Now to begin updating packages and using this freshly installed system....

:) Thanks again.

---

### Post by Jackie999 on 2008-10-10
Not sure if this is just my problem..or a problem with one of the intrepid updates I've taken.
Now when I plug in the usb device I'm getting this in dmesg:```
[  504.232133] usb 1-2: new full speed USB device using ohci_hcd and address 2
[  504.481480] usb 1-2: configuration #1 chosen from 1 choice
[  505.387380] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  505.414174] usbcore: registered new interface driver ndiswrapper

```Did it just load ndiswrapper ? Far as I know, I'd completely uninstalled that since it causes my lappy to freeze.

---

### Post by RaZoR1394 on 2008-10-10
The module is installed with the modules package during each kernel update. You've only removed the userspace part. Just blacklist ndiswrapper.

---

