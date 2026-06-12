---
title: "em28xx driver compilation in Intrepid (Beta)"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nickedynick on 2008-10-23
Hello everyone, hopefully there'll be someone out there with a decent answer to this.

In Hardy (and Gutsy and Feisty beforehand) I had my Pinnacle PCTV USB (DVB-T) stick installed and running fantastically using [this]("http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices") guide.

However, for some reason it wouldn't work once I installed the Intrepid beta - giving a few errors (similar to the ones at the end of the code below) on running the 'make' command.

After a bit of digging around and trying various methods I found a post [here]("http://ubuntuforums.org/showthread.php?t=740473&page=6") (#53) which seemed pretty hopeful. However, in a very similar way to most of the methods I've tried it gave a very familiar set of errors, ending in ```
make[1]: *** [default] Error 2
``` after using the 'make' command.

Below is the output from the last attempt, hopefully someone has had a similar experience and was more successful than me!

```
root@nick-laptop:/lib/firmware/v4l-dvb# make
make -C /lib/firmware/v4l-dvb/v4l 
make[1]: Entering directory `/lib/firmware/v4l-dvb/v4l'
No version yet, using 2.6.27-7-generic
make[1]: Leaving directory `/lib/firmware/v4l-dvb/v4l'
make[1]: Entering directory `/lib/firmware/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.27

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/lib/firmware/v4l-dvb/v4l'
make[1]: Entering directory `/lib/firmware/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.27-7-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
Kernel build directory is /lib/modules/2.6.27-7-generic/build
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/lib/firmware/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /lib/firmware/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tuner-types.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/mt20xx.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tda8290.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tea5767.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tea5761.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tda9887.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/tda827x.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/au0828-core.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-i2c.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-sram.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-eeprom.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-misc.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-hw-filter.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/flexcop-dma.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-driver.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-cards.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-if.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-risc.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-vbi.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-i2c.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-gpio.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-input.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/bttv-audio-hook.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cpia2_v4l.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cpia2_usb.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cpia2_core.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-driver.o
/lib/firmware/v4l-dvb/v4l/cx18-driver.c: In function 'cx18_request_module':
/lib/firmware/v4l-dvb/v4l/cx18-driver.c:568: warning: format not a string literal and no format arguments
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-cards.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-i2c.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-firmware.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-gpio.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-queue.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-streams.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-fileops.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-ioctl.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-controls.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-mailbox.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-vbi.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-audio.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-video.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-irq.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-av-core.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-av-audio.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-av-firmware.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-av-vbi.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-scb.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-dvb.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx18-io.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-cards.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-video.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-vbi.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-core.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-i2c.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-dvb.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx23885-417.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx25840-core.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx25840-audio.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx25840-firmware.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx25840-vbi.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-video.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-vbi.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-mpeg.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-cards.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-core.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-i2c.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-tvaudio.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/cx88-input.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvbdev.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dmxdev.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_net.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/dvb_math.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/av7110_hw.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/av7110_v4l.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/av7110_av.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/av7110_ca.o
  CC [M]  /lib/firmware/v4l-dvb/v4l/av7110.o
/lib/firmware/v4l-dvb/v4l/av7110.c: In function 'gpioirq':
/lib/firmware/v4l-dvb/v4l/av7110.c:698: error: implicit declaration of function 'swahw32'
make[3]: *** [/lib/firmware/v4l-dvb/v4l/av7110.o] Error 1
make[2]: *** [_module_/lib/firmware/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/lib/firmware/v4l-dvb/v4l'
make: *** [all] Error 2
```

---

### Post by mat1t on 2008-10-23
I get the same error, although mine worked previously. I'm working on trying to checkout an older version of the repository to see if that works. I'll let you know how I get on.

Mat

---

### Post by Nickedynick on 2008-10-23
Good plan, I'll try and have a look too. Cheers for the response :)

---

### Post by mat1t on 2008-10-23
I went back a bit and tried revision 9300 and it worked, I'm going to edge forwards and see if I can find the most recent one where it builds.

Mat

```
hg revert --all -r 9300
```

---

### Post by Nickedynick on 2008-10-23
Thanks for your help Mat.

Unfortunately it's still not working properly - I get the following output:
```
root@nick-laptop:/lib/firmware/driver/v4l-dvb-kernel# make
make -C /lib/firmware/driver/v4l-dvb-kernel/v4l 
make[1]: Entering directory `/lib/firmware/driver/v4l-dvb-kernel/v4l'
scripts/make_makefile.pl
No version yet.
Updating/Creating .config
File not found: /lib/modules/2.6.27-7-generic/build/.config at ./scripts/make_kconfig.pl line 30.
make[1]: Leaving directory `/lib/firmware/driver/v4l-dvb-kernel/v4l'
make[1]: Entering directory `/lib/firmware/driver/v4l-dvb-kernel/v4l'
Updating/Creating .config
File not found: /lib/modules/2.6.27-7-generic/build/.config at ./scripts/make_kconfig.pl line 30.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'. Stop.
make[1]: Leaving directory `/lib/firmware/driver/v4l-dvb-kernel/v4l'
make: *** [all] Error 2
```

Which guide were you using?

Nick

---

### Post by mat1t on 2008-10-23
I have a different card to you, so the minor details are different. I hadn't read that you're using a different repository to me.

Instead of hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental) I'm doing hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

The guide I was using was from [http://forum.ubuntuusers.de/topic/hauppauge-wintv-nova-hd-s2-einrichten/3/](http://forum.ubuntuusers.de/topic/hauppauge-wintv-nova-hd-s2-einrichten/3/)

Revision 9338 compiles for me.

---

### Post by Nickedynick on 2008-10-23
Cool, thanks. It now compiles and installs. For the sake of anyone else in this situation, I used this sequence:

```
sudo su
apt-get install mercurial gcc build-essential linux-source linux-headers-`uname -r` kaffeine
cd /lib/firmware
wget http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz
tar zxvf firmware_v3.tgz
mkdir driver
cd driver
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
hg revert --all -r 9338
make
make install

[REBOOT]

modprobe em28xx
```

However... Kaffeine now won't recognise the card and looking at dmesg after unplugging and plugging it back in again gave this:

```
[ 1143.939427] em28xx #0: disconnecting em28xx #0 video
[ 1143.939438] em28xx #0: device /dev/video1 is open! Deregistration and memory deallocation are deferred on close.
[ 1145.908115] usb 5-2.4: new high speed USB device using ehci_hcd and address 10
[ 1146.003707] usb 5-2.4: configuration #1 chosen from 1 choice
[ 1146.004299] em28xx new video device (eb1a:2870): interface 0, class 255
[ 1146.004313] em28xx Doesn't have usb audio class
[ 1146.004316] em28xx #1: Alternate settings: 8
[ 1146.004320] em28xx #1: Alternate setting 0, max size= 0
[ 1146.004324] em28xx #1: Alternate setting 1, max size= 0
[ 1146.004328] em28xx #1: Alternate setting 2, max size= 1448
[ 1146.004333] em28xx #1: Alternate setting 3, max size= 2048
[ 1146.004338] em28xx #1: Alternate setting 4, max size= 2304
[ 1146.004342] em28xx #1: Alternate setting 5, max size= 2580
[ 1146.004346] em28xx #1: Alternate setting 6, max size= 2892
[ 1146.004350] em28xx #1: Alternate setting 7, max size= 3072
[ 1146.004700] em28xx #1: em28xx chip ID = 35
[ 1146.270043] em28xx #1: i2c eeprom 00: 1a eb 67 95 1a eb 70 28 c0 12 81 00 6a 22 00 00
[ 1146.270068] em28xx #1: i2c eeprom 10: 00 00 04 57 02 0d 00 00 00 00 00 00 00 00 00 00
[ 1146.270085] em28xx #1: i2c eeprom 20: 44 00 00 00 f0 10 02 00 00 00 00 00 5b 00 00 00
[ 1146.270102] em28xx #1: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 3b 33 31 4a
[ 1146.270119] em28xx #1: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270136] em28xx #1: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270153] em28xx #1: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 22 03 55 00 53 00
[ 1146.270170] em28xx #1: i2c eeprom 70: 42 00 20 00 32 00 38 00 37 00 30 00 20 00 44 00
[ 1146.270186] em28xx #1: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 00 00 00 00 00 00
[ 1146.270203] em28xx #1: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270220] em28xx #1: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270237] em28xx #1: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270254] em28xx #1: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270271] em28xx #1: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270287] em28xx #1: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270304] em28xx #1: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1146.270322] EEPROM ID= 0x9567eb1a, hash = 0x2b5e8bc3
[ 1146.270325] Vendor/Product ID= eb1a:2870
[ 1146.270328] No audio on board.
[ 1146.270330] 500mA max power
[ 1146.270334] Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 1146.299795] em28xx #1: found i2c device @ 0xa0 [eeprom]
[ 1146.305797] em28xx #1: found i2c device @ 0xc0 [tuner (analog)]
[ 1146.317425] em28xx #1: Your board has no unique USB ID and thus need a hint to be detected.
[ 1146.317435] em28xx #1: You may try to use card=<n> insmod option to workaround that.
[ 1146.317439] em28xx #1: Please send an email with this log to:
[ 1146.317442] em28xx #1: 	V4L Mailing List <video4linux-list@redhat.com>
[ 1146.317446] em28xx #1: Board eeprom hash is 0x2b5e8bc3
[ 1146.317449] em28xx #1: Board i2c devicelist hash is 0x4b800080
[ 1146.317452] em28xx #1: Here is a list of valid choices for the card=<n> insmod option:
[ 1146.317459] em28xx #1:     card=0 -> Unknown EM2800 video grabber
[ 1146.317463] em28xx #1:     card=1 -> Unknown EM2750/28xx video grabber

[ 1146.317466] em28xx #1:     card=2 -> Terratec Cinergy 250 USB
[ 1146.317470] em28xx #1:     card=3 -> Pinnacle PCTV USB 2
[ 1146.317473] em28xx #1:     card=4 -> Hauppauge WinTV USB 2
[ 1146.317477] em28xx #1:     card=5 -> MSI VOX USB 2.0
[ 1146.317480] em28xx #1:     card=6 -> Terratec Cinergy 200 USB
[ 1146.317485] em28xx #1:     card=7 -> Leadtek Winfast USB II
[ 1146.317488] em28xx #1:     card=8 -> Kworld USB2800
[ 1146.317492] em28xx #1:     card=9 -> Pinnacle Dazzle DVC 90/DVC 100
[ 1146.317496] em28xx #1:     card=10 -> Hauppauge WinTV HVR 900
[ 1146.317499] em28xx #1:     card=11 -> Terratec Hybrid XS
[ 1146.317502] em28xx #1:     card=12 -> Kworld PVR TV 2800 RF
[ 1146.317506] em28xx #1:     card=13 -> Terratec Prodigy XS
[ 1146.317510] em28xx #1:     card=14 -> Pixelview Prolink PlayTV USB 2.0
[ 1146.317514] em28xx #1:     card=15 -> V-Gear PocketTV
[ 1146.317517] em28xx #1:     card=16 -> Hauppauge WinTV HVR 950
[ 1146.317521] em28xx #1:     card=17 -> Pinnacle PCTV HD Pro Stick
[ 1146.317525] em28xx #1:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[ 1146.317528] em28xx #1:     card=19 -> PointNix Intra-Oral Camera
[ 1146.317532] em28xx #1:     card=20 -> AMD ATI TV Wonder HD 600
[ 1146.317537] em28xx #1:     card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder
[ 1146.317540] em28xx #1:     card=22 -> Unknown EM2750/EM2751 webcam grabber
[ 1146.317544] em28xx #1:     card=23 -> Huaqi DLCW-130
[ 1146.317548] em28xx #1:     card=24 -> D-Link DUB-T210 TV Tuner
[ 1146.317551] em28xx #1:     card=25 -> Gadmei UTV310
[ 1146.317555] em28xx #1:     card=26 -> Hercules Smart TV USB 2.0
[ 1146.317558] em28xx #1:     card=27 -> Pinnacle PCTV USB 2 (Philips FM1216ME)
[ 1146.317562] em28xx #1:     card=28 -> Leadtek Winfast USB II Deluxe
[ 1146.317566] em28xx #1:     card=29 -> Pinnacle Dazzle DVC 100
[ 1146.317569] em28xx #1:     card=30 -> Videology 20K14XUSB USB2.0
[ 1146.317573] em28xx #1:     card=31 -> Usbgear VD204v9
[ 1146.317576] em28xx #1:     card=32 -> Supercomp USB 2.0 TV
[ 1146.317580] em28xx #1:     card=33 -> SIIG AVTuner-PVR/Prolink PlayTV USB 2.0
[ 1146.317585] em28xx #1:     card=34 -> Terratec Cinergy A Hybrid XS
[ 1146.317588] em28xx #1:     card=35 -> Typhoon DVD Maker
[ 1146.317592] em28xx #1:     card=36 -> NetGMBH Cam
[ 1146.317595] em28xx #1:     card=37 -> Gadmei UTV330
[ 1146.317599] em28xx #1:     card=38 -> Yakumo MovieMixer
[ 1146.317603] em28xx #1:     card=39 -> KWorld PVRTV 300U
[ 1146.317606] em28xx #1:     card=40 -> Plextor ConvertX PX-TV100U
[ 1146.317610] em28xx #1:     card=41 -> Kworld 350 U DVB-T
[ 1146.317614] em28xx #1:     card=42 -> Kworld 355 U DVB-T
[ 1146.317617] em28xx #1:     card=43 -> Terratec Cinergy T XS
[ 1146.317621] em28xx #1:     card=44 -> Terratec Cinergy T XS (MT2060)
[ 1146.317624] em28xx #1:     card=45 -> Pinnacle PCTV DVB-T
[ 1146.317629] em28xx #1:     card=46 -> Compro, VideoMate U3
[ 1146.317632] em28xx #1:     card=47 -> KWorld DVB-T 305U
[ 1146.317636] em28xx #1:     card=48 -> KWorld DVB-T 310U
[ 1146.317639] em28xx #1:     card=49 -> MSI DigiVox A/D
[ 1146.317643] em28xx #1:     card=50 -> MSI DigiVox A/D II
[ 1146.317646] em28xx #1:     card=51 -> Terratec Hybrid XS Secam
[ 1146.317650] em28xx #1:     card=52 -> DNT DA2 Hybrid
[ 1146.317653] em28xx #1:     card=53 -> Pinnacle Hybrid Pro
[ 1146.317658] em28xx #1:     card=54 -> Kworld VS-DVB-T 323UR
[ 1146.317661] em28xx #1:     card=55 -> Terratec Hybrid XS (em2882)
[ 1146.317665] em28xx #1:     card=56 -> Pinnacle Hybrid Pro (2)
[ 1146.317668] em28xx #1:     card=57 -> Kworld PlusTV HD Hybrid 330
[ 1146.317673] em28xx #1:     card=58 -> Compro VideoMate ForYou/Stereo
[ 1146.856280] em28xx #1: V4L2 device registered as /dev/video2 and /dev/vbi1
[ 1146.856290] em28xx-audio.c: probing for em28x1 non standard usbaudio
[ 1146.856293] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[ 1146.856900] em28xx #1: Found Unknown EM2750/28xx video grabber
```

Looks like I'm getting there slowly...

---

