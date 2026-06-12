---
title: "Lucid Lynx install, w/ volume but no sound, ATI Tech Inc IXP SB4x0 HD Aud Ctlr rev01"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by kohrime on 2010-05-29
Hi! I'm relatively new at Ubuntu & Linux. I just installed Lucid Lynx and I'm currently having problem of having no sound at all in my laptop (ECS Elitegroup W341UI). 

Actually, I first installed Karmic Koala like 2 months ago and it still has that same problem that it didn't had any sound even though there is volume control and is not muted. I never gotten the sound to work in Karmic. When I heard the Lucid Lynx was out, I installed that and it didn't have any sound.

[Here's a screenshot that it does have volume]("http://i48.tinypic.com/238qag.png") but it doesn't output any sound when I'm playing videos or mp3s.

I tried reading this guide - [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) - but still no avail. Tried aplay Front_Left.wav & Front_Right.wav but it doesn't play  anything at all. In that troubleshooting tutorial, where the info is asked in ALSA I got this link - [http://www.alsa-project.org/db/?f=c9d9b3b82576f3e05f516b7561189ea574c96e2c](http://www.alsa-project.org/db/?f=c9d9b3b82576f3e05f516b7561189ea574c96e2c) 

Here is also the lspci of my laptop: 
```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```I'm quite sure the sound should be okay as it's currently dualboot with Windows XP and it didn't have problems with the the audio in that OS. It only happens when I've installed Ubuntu Karmic and now Ubuntu Lucid.

After countless google & search in this forums for a solution, I haven't found anything to solve this problem at all OTL I'm sorry but I'm honestly quite a n00b still in Linux so I'm not sure if what I'm doing is correct, just endlessly reading and learning here and there ^^;;

Any help to solve this problem will be much appreciated *bows deeply*

Ais

---

### Post by lrgmmc on 2010-05-29
can you post your ```
aplay -l
```

---

### Post by kohrime on 2010-05-29
Hi lrgmmc and thanks for replying :D

Here is aprl -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```o.o different? (Okay, sorry, I don't get it OTL)

---

### Post by lrgmmc on 2010-05-29
post ```
cat /proc/asound/version
```

---

### Post by kohrime on 2010-05-29
Here is my cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

---

### Post by lrgmmc on 2010-05-29
ok i came across a couple posts that said to upgrade alsa.
[HTML]http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/[/HTML]same sound card as hp mini note 1000. please report back to let us know how it goes.

---

### Post by kohrime on 2010-05-29
Okay, thanks lrgmmc :) Will update you how this goes *crosses fingers*

---

### Post by kohrime on 2010-05-30
OTL I did everything on the tutorial (even though there were some warnings I noticed here and there during the compilation but not that alarming that will be giving it a halt) but to my dismay still no audio OTL

I checked my cat /proc/asound/version now and it is now really upgraded to 1.0.23
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 30 2010 for kernel 2.6.32-21-generic (SMP).
```The aplay -l looks like this
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```The lspci looks like this
```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```Kindly please help to solve this *bows deeply*

[Just tested and checked the sound preferences](http://i46.tinypic.com/20b1tl4.png) and it does detect the player. I'm sure I'm not deaf but I can't hear anything coming out from the speakers of the laptop nor when I plugged in my earphones OTL Kindly help please *bows deeply*

---

### Post by lrgmmc on 2010-05-30
here is another suggestion i found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/comments/11](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/comments/11)  it is the same as above except a few changes when compiling. try that and let me know.

---

### Post by kohrime on 2010-05-30
[Just checked and it's not muted there...](http://i46.tinypic.com/157ez9y.png)

---

### Post by lrgmmc on 2010-05-30
if all fails we can have you try updating your kernel.that worked on my netbook.
[http://ubuntuforums.org/showpost.php?p=9379528&postcount=208](http://ubuntuforums.org/showpost.php?p=9379528&postcount=208)

---

### Post by kohrime on 2010-05-30
I just did :) Okay, will try compiing & downgrading then :) Or wait, should I just do editing of alsa-base.conf?

---

### Post by lrgmmc on 2010-05-30
well there were some diffrent ./configure options that were needed so i would do it again then.

---

### Post by kohrime on 2010-05-30
Okay :) 

Anyway, I was in the middle of this task (compiling)
```
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname  -r)
```


when it gave me this error
```
  CC [M]  /home/zeldais/alsa-driver-1.0.19/acore/memory.o
  CC [M]  /home/zeldais/alsa-driver-1.0.19/acore/info.o
/home/zeldais/alsa-driver-1.0.19/acore/info.c: In function &#8216;snd_info_entry_prepare&#8217;:
/home/zeldais/alsa-driver-1.0.19/acore/info.c:161: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/home/zeldais/alsa-driver-1.0.19/acore/info.c: In function &#8216;snd_info_register&#8217;:
/home/zeldais/alsa-driver-1.0.19/acore/info.c:1020: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
make[3]: *** [/home/zeldais/alsa-driver-1.0.19/acore/info.o] Error 1
make[2]: *** [/home/zeldais/alsa-driver-1.0.19/acore] Error 2
make[1]: *** [_module_/home/zeldais/alsa-driver-1.0.19] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [compile] Error 2
```
OTL

---

### Post by lrgmmc on 2010-05-30
you re downloaded the files right?

---

### Post by kohrime on 2010-05-30
Yeah, I downloaded the files and I mean, when I enter "make" at the terminal, it gave that error OTL

---

### Post by lrgmmc on 2010-05-30
you might have to remove the old ones ```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
``` 
then try again

---

### Post by kohrime on 2010-05-30
I just removed them with the commands you gave me and entered it at the terminal. Entered "make" but still the same error as above -

```
  CC [M]  /home/zeldais/alsa-driver-1.0.19/acore/info.o
/home/zeldais/alsa-driver-1.0.19/acore/info.c: In function ‘snd_info_entry_prepare’:
/home/zeldais/alsa-driver-1.0.19/acore/info.c:161: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/zeldais/alsa-driver-1.0.19/acore/info.c: In function ‘snd_info_register’:
/home/zeldais/alsa-driver-1.0.19/acore/info.c:1020: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/home/zeldais/alsa-driver-1.0.19/acore/info.o] Error 1
make[2]: *** [/home/zeldais/alsa-driver-1.0.19/acore] Error 2
make[1]: *** [_module_/home/zeldais/alsa-driver-1.0.19] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [compile] Error 2
```OTL

I just realized when I do the command ```
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname  -r)
```

I get this
```
checking for current directory... /home/zeldais/alsa-driver-1.0.19
checking cross compile... 
checking for directory with kernel source... ./configure: line 4820: cd: /usr/src/linux-headers-: No such file or directory
/usr/src/linux-headers-
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.32-21-generic/build).
```

---

### Post by lrgmmc on 2010-05-30
ok now i think it is a good time to just upgrade you kernel. not that hard either.
```
 [I]mkdir 2.6.34 
cd 2.6.34 
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb")
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb")
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb")
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb")[/I]
sudo dpkg -i *.deb

```

---

### Post by kohrime on 2010-05-30
Will do that now :D Thank you so much for helping me lrgmmc :'D

---

### Post by kohrime on 2010-05-30
I just finished installing the new kernel as you instructed. Should I get back in installing the alsa-driver-1.0.19? ^^;;

---

### Post by lrgmmc on 2010-05-30
need to reboot. then test if audio if not the ya start the installing.

---

### Post by kohrime on 2010-05-30
Rebooted but it said something like "ureadhead" something something at the beginning before going to the main OS o.o

Anyway, I entered this at terminal 
```
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-
```
And it still gave me this
```
checking for current directory... /home/zeldais/alsa-driver-1.0.19
checking cross compile... 
checking for directory with kernel source... ./configure: line 4820: cd: /usr/src/linux-headers-: No such file or directory
/usr/src/linux-headers-
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.34-020634-generic/build).
```OTL

Edit: And oh, I can't hear anything at the speakers of my laptop still OTL

---

### Post by lrgmmc on 2010-05-30
```
[SIZE=2]lspci -v[/SIZE]

```
and post

---

### Post by kohrime on 2010-05-30
Here's the lspci -v
```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0000000-c00fffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 0000000038000000-00000000381fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
    I/O behind bridge: 00006000-00007fff
    Memory behind bridge: b0000000-b1ffffff
    Prefetchable memory behind bridge: 00000000b2000000-00000000b3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0504000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
    Subsystem: Rioworks Device 205f
    Flags: 66MHz, medium devsel
    I/O ports at 8400 [size=16]
    Memory at c0507000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Rioworks Device 205f
    Flags: bus master, slow devsel, latency 64, IRQ 27
    Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
    Subsystem: Rioworks Device 205f
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]

    Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
    Subsystem: Rioworks Device 2054
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at c0100000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at a000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8225
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at b000 [size=256]
    Memory at c0200000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: rtl8180
    Kernel modules: rtl8180
``` 

Hmm...

---

### Post by lrgmmc on 2010-05-30
ok i will get back on later today got to get back to work. but i'll keep looking and we'll find a solution.

---

### Post by kohrime on 2010-05-30
Thanks a whole bunch :D I subscribed to this thread through email now :) Take care with work :D

---

### Post by lrgmmc on 2010-05-30
ok maybe we will make some better head way today. so if you could post the output from ```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by kohrime on 2010-05-30
cat /proc/asound/card0/codec#* | grep Codec outputted
```
Codec: SigmaTel STAC9200
Codec: LSI ID 1040
```

Thanks again :D

---

### Post by lrgmmc on 2010-05-30
ok try this ```
sudo nano /etc/modprobe.d/alsa-base.conf
```and if you see 
```
options snd-hda-intel model=xxxx
```change it to look like 
```
options snd-hda-intel model=oqo
```if it's not there add it to the end of the file. save and reboot.
 there are other models to choose so if it dont work try these as well 
```
dell-d21
dell-d22
dell-d23
dell-m21
dell-m22
dell-m23
dell-m24
dell-m25
dell-m26
dell-m27
gateway-m4
gateway-m4-2
panasonic

```i know it is a lot to try but it is what this site sugested [HTML]https://help.ubuntu.com/community/HdaIntelSoundHowto[/HTML]and i got the model from this site [HTML]http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt[/HTML] good luck

---

### Post by kohrime on 2010-05-30
Yes! Finally! Finally the audio worked! *confettis* Thanks a whole lot lrgmmc! Your first suggestion did the job already! Yes! ^_____^

To summarize, next time I fresh install Lucid Lynx, I will just do your last post to make the audio work, right? (edit only the alsa-base.conf?)

---

### Post by lrgmmc on 2010-05-30
that sound right. so that is what i would do now since we change a lot of stuff. freash install and then edit the alsa-base.conf.

---

### Post by lrgmmc on 2010-05-30
well have a good day or night. oh and if you have any q's just pm me and i will be glade to help. oh and mark the forum as solved.

---

### Post by kohrime on 2010-05-30
Yeah, there were lots of changes done so that's what I'm going to do first thing tomorrow, fresh install Lucid Lynx XD

Again, I humbly and sincerely thank you for your patience and your big big help in solving my audio problem lrgmmc *bows very deeply*

---

### Post by buvesz on 2010-07-15
Hi. I have the exact same problem as you. With the same soundcard :

When you edited the alsa-base.conf file, what did you put in the end ?

```
options snd-hda-intel model=oqo
```

or one of those other models ?

```
dell-d21
dell-d22
dell-d23
dell-m21
dell-m22
dell-m23
dell-m24
dell-m25
dell-m26
dell-m27
gateway-m4
gateway-m4-2
panasonic
```

---

### Post by kohrime on 2010-07-22
Hi buvesz ^_^

I only changed that first suggestion and the sound worked :3

options snd-hda-intel model=oqo

---

