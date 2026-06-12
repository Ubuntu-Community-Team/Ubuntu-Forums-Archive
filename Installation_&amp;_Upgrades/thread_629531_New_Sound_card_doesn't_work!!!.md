---
title: "New Sound card doesn't work!!!"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Legendário on 2007-12-02
I have a P4 2,26ghz with 256mb of ram. My MB is an Asus P4VP-MX. The onboard sound card on the computer was not working even on Windows XP (i got the pc from someone else) so i decided to buy a new sound card. I bought a Creative Labs ES1371/1373 but now I can't make it work. The drivers seems to be loaded but the system keeps telling me that it can't find a sound device. I tried to install the linux-ubuntu-modules-2.6.22-386 package from synaptic but it didn't help.

Please, I am hopeless. No one in the Ubuntu Forum from my country seems to know how to solve this. Here are the output of some comands that may help to analise it.

```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```

```
$ lspci -vvnn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. P4M266 Host Bridge [1106:3148]
        Subsystem: ASUSTeK Computer Inc. Unknown device [1043:807b]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 8
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ff800000-ff9fffff
        Prefetchable memory behind bridge: cff00000-dfefffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:0b.0 Multimedia audio controller [0401]: Ensoniq 5880 AudioPCI [1274:5880] (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128 [1274:2000]
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at e080 [size=64]
        Capabilities: <access denied>

00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard [1043:80a1]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard [1043:80a1]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 16
        Region 4: I/O ports at e480 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard [1043:80a1]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin C routed to IRQ 16
        Region 4: I/O ports at ec00 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard rev 1.01 [1043:80a1]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 128 bytes
        Interrupt: pin D routed to IRQ 16
        Region 0: Memory at ffaff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard [1043:80a1]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard rev. 1.01 [1043:80a1]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 255
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        Region 4: I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
        Subsystem: ASUSTeK Computer Inc. Unknown device [1043:80ff]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (750ns min, 2000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at e800 [size=256]
        Region 1: Memory at ffaffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: S3 Inc. VT8375 [ProSavage8 KM266/KL266] [5333:8d04] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device [1043:807b]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1000ns min, 63750ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at ff980000 (32-bit, non-prefetchable) [size=512K]
        Region 1: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at ff970000 [disabled] [size=64K]
        Capabilities: <access denied>

```

```
lsmod | grep snd
snd_ens1371            26144  0 
gameport               15240  1 snd_ens1371
snd_ac97_codec         99492  1 snd_ens1371
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                77320  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31872  0 
snd_seq_midi            8704  0 
snd_rawmidi            24832  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22916  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    52356  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10504  1 snd_pcm

```

```
aplay -l
aplay: device_list:204: nenhuma placa de som encontrada...

``` translating this one: no sound device found...

```
~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

I hope i'll find the solution here. I don't want to waste the money i spent on a new sound card... :(

Thanks

---

### Post by Pumalite on 2007-12-02
Post:
sudo lshw -C sound

---

### Post by tibellus on 2007-12-02
Hey, same problem here! I'll paste the output for the command you suggested and maybe you can help me out, please! It seems here it somewhat partially unsolved... because I have sound on pidgin and exaile but on sites like Youtube i have nothing!

```
sudo lshw -C sound
  *-multimedia:0          
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:1
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 40
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
```

I hope it will work...

---

### Post by Pumalite on 2007-12-02
Try:
sudo apt-get install linux-backports-modules-generic

---

### Post by tibellus on 2007-12-02
What will happen after i install that? And what should I do next?

---

### Post by Pumalite on 2007-12-02
Check in the Terminal:
alsamixer

---

### Post by tibellus on 2007-12-02
I've checked, it uses the onboard sound card. Still no sound on Youtube... I plugged the headphones into the onboard sound card and I have sound on every application but with an annoying hiss included :D I can even hear my keyboard making sounds!! or the mouse scroll!!

---

### Post by Pumalite on 2007-12-02
Her is collection of possible solutions:

No sound after installation of Gutsy
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

### Post by Legendário on 2007-12-02
Here is the output of the command you asked me. Hope it helps...

```
 sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 5880 AudioPCI
       vendor: Ensoniq
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=128 mingnt=12

```

---

### Post by Pumalite on 2007-12-02
Run:
sudo apt-get install linux-backports-modules-generic
Then test your alsamixer

---

### Post by Legendário on 2007-12-02
> **Pumalite said:**
> Run:
sudo apt-get install linux-backports-modules-generic
Then test your alsamixer
tried this but didn't work... so what is next?

```
$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by Pumalite on 2007-12-02
Try the rest of the possible solutions that I posted.

---

### Post by Legendário on 2007-12-02
Here,

i tried to run a Ubuntu live-cd and type alsamixer in the terminal. Guess what? I got the same error... I guess it is not supported by standard.

Another thing... I am trying to compile the alsa driver but i am getting this error below:

```
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make all-deps
make[1]: Entrando no diretório `/home/kemel/Downloads/alsa/alsa-driver-1.0.15'
make[1]: Nada a ser feito para `all-deps'.
make[1]: Saindo do diretório `/home/kemel/Downloads/alsa/alsa-driver-1.0.15'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/kemel/Downloads/alsa/alsa-driver-1.0.15/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: não é possível criar o diretório `/include': Permissão negada
install: impossível fazer stat em `include/sound/*.h': Arquivo ou diretório inexistente
make: ** [install-headers] Erro 1

```

what is it?

---

### Post by Legendário on 2007-12-03
> No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine

Pumalite, i need your help here. I tried compiling the alsa-driver from the alsa web site, but it didn't work againg. The problem is not from driver's because the card is supported by the alsa project, and they are loaded correctly, etc, but the system keeps telling me i have no card, altought lspci shows me the right sound card. It must be some configuration problem. How can I add the sound card. See:
 ```
$ asoundconf list
Names of available sound cards:
```
As you can see, it shows no device... How can i add it with the ```
asoundconf set-default-card soundcard
```
How should i replace the soundcard on the string? Should i write the name, a code or what?

Thanks for the help.

---

### Post by Pumalite on 2007-12-03
You must know what your card is.

---

### Post by Legendário on 2007-12-05
I know what my card is but i don't know the syntax of the command. :confused: Could you help?

---

### Post by Pumalite on 2007-12-05
Just put the name as in: Intel  82801EB/ER (ICH5/ICH5R) as example.

---

### Post by Legendário on 2007-12-05
> **Pumalite said:**
> Just put the name as in: Intel  82801EB/ER (ICH5/ICH5R) as example.

```
$ asoundconf set-default-card soundcard Ensoniq 5880 AudioPCI
You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

kemel@P4-Kemel:~$ asoundconf list
Names of available sound cards:

```

---

### Post by Legendário on 2007-12-09
Can anyone else help me here???

---

