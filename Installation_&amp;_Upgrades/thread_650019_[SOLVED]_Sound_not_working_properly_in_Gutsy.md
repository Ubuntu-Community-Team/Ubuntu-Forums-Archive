---
title: "[SOLVED] Sound not working properly in Gutsy"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by jonamoen on 2007-12-25
Well, hello. I know I'm not the only one having problems with the sound on my computer after installing Gutsy but here goes anyway.

I have searched the whole forum and spent the whole day trying to get any, ANY, sound from my laptop (Toshiba satellite A-100-699); first installing and compiling ALSA several times, then going over to OSS. After the OSS-install I got the sound for, well, like 5 minutes. Then Amarok crashed on me (for reasons unknown) and after the sound has been like a badly tuned radio (noisy). I can play music in Rhythmbox and Totem but Amarok was silent like the grave (so I uninstalled it).

Some pastes:

aplay -l returns:
```
********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [ATI HD Audio], device 0: OSS ID [High Definition Audio front]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [ATI HD Audio], device 1: OSS ID [High Definition Audio center/LFE]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [ATI HD Audio], device 2: OSS ID [High Definition Audio rec]
  Subdevices: 1/1
  Subdevice #0: OSS subname
```

lspci -v returns:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 24000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at c0004400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 20000000-23ffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 22
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7094
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 28000000-2bfff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at a000 [size=256]
        Memory at c0215000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at c0215800 (32-bit, non-prefetchable) [size=2K]
        Memory at c0210000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

lsmod returns:
```
Module                  Size  Used by
wlan_wep                8064  1 
af_packet              24840  4 
ipv6                  273892  8 
fglrx                 656352  11 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vmix                   14132  0 
ossusb                 56072  0 
hdaudio               103572  0 
osscore               566196  3 vmix,ossusb,hdaudio
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
ac                      6148  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
wlan_scan_sta          15104  1 
ath_rate_sample        14208  1 
pcmcia                 41388  0 
ath_pci                98336  0 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
pcspkr                  4224  0 
8139too                27776  0 
usbhid                 29536  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
hid                    28928  1 usbhid
serio_raw               8068  0 
psmouse                39952  0 
wlan                  206660  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192720  3 ath_rate_sample,ath_pci
i2c_piix4               9740  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_piix4
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               36492  0 
atiixp                  7056  0 [permanent]
ide_core              116804  2 ide_cd,atiixp
ohci_hcd               22916  0 
usbcore               138632  5 ossusb,usbhid,ehci_hcd,ohci_hcd
sata_sil               12168  2 
ata_generic             8452  0 
libata                125168  2 sata_sil,ata_generic
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

I highly appreciate any help :)

---

### Post by Pumalite on 2007-12-25
Have you tried:
sudo apt-get install linux-backports-modules-generic

---

### Post by jonamoen on 2007-12-25
Didn't change anything :(

---

### Post by Pumalite on 2007-12-25
Did you compile the latest alsa-driver? (xx.15)

---

### Post by jonamoen on 2007-12-25
Yes, but that did not give me any sound. Uninstalled ALSA when I switched to OSS.

---

### Post by Pumalite on 2007-12-25
See if you can get something out of these: (a collection from different posts on the subject):

 Re: [SOLVED] No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine
And i used this command to test my surround 5.1:
Quote:
speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work
__________________
Reply With Quote
 Re: [SOLVED] No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine
And i used this command to test my surround 5.1:
Quote:
speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work
__________________
Reply With Quote
[http://ubuntuforums.org/showthread.php?t=616846](http://ubuntuforums.org/showthread.php?t=616846)
[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6)
[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

 Re: No sound with Hda-intel
got it working! wow, only took me four months! yeah enough of my whining, I know. Here's how *I* did it:

(NOTE: I know this works with my Lenovo 3000 N100 0768 E7U, I'm not guaranteeing that it works with any other model/variant)

Code:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=3stack

Save the file, close it, reboot, and CROSS YOUR FINGERS!

As usual, if there's no sound initially, open the volume control and make sure nothing is muted. Also, open the volume control(doubleclick the speaker), click File->change device, select the OSS mixer, and make sure none of those output channels are muted either. If none of these work for you, then you can try PM'ing me, but I'm pretty new to this still.

Much of this comes from the howto at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Note: Initially, because I had fiddled with it so much, I had nothing detected - a red X next to the volume control, would tell me I had no sound card when I tried to adjust volume. To get rid of that, I ran "sudo apt-get install linux-backports-modules-generic" as suggested by Pumalite, and it restored it to (what appears to be) the default - sound card looks like it's working, but you can't hear sound out of anything.

 Re: [SOLVED] No sound after installation of Gutsy
I have finally solved the problem after a lot of playing around. The answer was very simple - go to the volume control icon in the right hand corner of the screen, open the Alsa mixer, select the switches tab and uncheck the 'Audigy Analog/Digital Output Jack' option. This must be happening to a lot of people trying Ubuntu for the first time. Does anyone know why this is selected on as Default? Surely most people use analogue speakers as default? As always thanks for the help.

 Re: [SOLVED] No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine
And i used this command to test my surround 5.1:
Quote:
speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work
__________________
Reply With Quote

---

### Post by jonamoen on 2007-12-26
```
sudo asoundconf list

Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.
```

Tried this thread: [http://ubuntuforums.org/showthread.php?p=3588321#post3588321](http://ubuntuforums.org/showthread.php?p=3588321#post3588321)

ALSA compiled successfully but at the end it stated that ALSA is muted by default. Can't open alsamixer:

```
sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

Other tests:

```
cat /proc/asound/cards 
cat: /proc/asound/cards: No such file or directory

```

My user has permission to use sound. When I click the 'test' button in Sound-prefs I can hear the sound right after a reboot but not if I have use the computer for a while (10 mins+). Get system sounds (beep) when doing something wrong (erasing something that isn't...).

Arg, this is getting annoying. :(

Edit: *Might the reason be that when I try to manage the volume I get an error saying that 'No volume control Gstreamer plugins and/or devices found.' ?!?*

---

### Post by Pumalite on 2007-12-26
If you compile alsa successfully, you should be able to open it.

---

### Post by jonamoen on 2007-12-26
```
 cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
```

Might this be the fault?

---

### Post by Pumalite on 2007-12-26
Could be. Why don't you recompile following my guide in prior post?

---

### Post by jonamoen on 2007-12-26
I did follow the guide. No sound now.

alsamixer returns: 
```
********************   WARNING   *******************************
Warning! alsamixer uses ALSA emulation instead of the native OSS API
****************************************************************

snd_mixer_set_callback()
No mixer elems found
```

sudo gedit /etc/modprobe.d/alsa-base had 'options snd-hda-intel probe_mask=8 model=3stack' before I followed the guide.

Should I remove OSS or? and if so, how do I do that?

---

### Post by Pumalite on 2007-12-26
I believe OSS and alsa can coexist.I'm out of my depth here. Hopefully someone will chime in.

---

### Post by jonamoen on 2007-12-26
Oh, ok. Thank you anyway :)

---

### Post by Pumalite on 2007-12-26
You are welcome. Good luck! Sorry I couldn't be of more help.

---

### Post by jonamoen on 2007-12-26
Compiled ALSA again and got the sound to work. I'm happy as 5-year old on christmas eve :) Thanks to the guys at the #alsa channel :)

---

### Post by Pumalite on 2007-12-26
I'm very glad you got it working!

---

### Post by lancest on 2007-12-27
> **Pumalite said:**
> 
 Re: No sound with Hda-intel
got it working! wow, only took me four months! yeah enough of my whining, I know. Here's how *I* did it:

(NOTE: I know this works with my Lenovo 3000 N100 0768 E7U, I'm not guaranteeing that it works with any other model/variant)

Code:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=3stack

Save the file, close it, reboot, and CROSS YOUR FINGERS!
__________________
Reply With Quote
Same card
I tried this twice but I don't end up with an [SIZE="5"]alsa-base[/SIZE] file in modprobe.  Sound has as worked before using 1.0.14.

---

### Post by Pumalite on 2007-12-27
(NOTE: I know this works with my Lenovo 3000 N100 0768 E7U, I'm not guaranteeing that it works with any other model/variant)

---

