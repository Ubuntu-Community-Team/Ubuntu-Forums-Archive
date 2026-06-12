---
title: "No sound with Hda-intel"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by aws910 on 2007-11-12
I did a clean-install of Gutsy and did all updates.  No sound for hda-intel.

I know a lot of people have had problems getting HDA-Intel sound to work, and there are many supposed "fixes".  I've tried the following:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_FPG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_FPG)
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
...and many others(cant remember them all anymore)

My machine is a Lenovo 3000 N100 0768-E7U.  Here's the pertinent lspci -vv output:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 2066
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

```

After trying all those "fixes", it actually made things worse.  Now alsa won't even recognize that any devices are present.  when I try to run amixer I get this:
```
amixer: Mixer attach default error: No such device
```
In the BIOS I checked, and all features are turned on so it's not disabled there.

When I try doing "sudo modprobe snd-hda-intel" at the end of all these fixes, I get this:
```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
results of dmesg | tail:
```
[  975.364000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  975.364000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  975.364000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  975.364000] snd_hda_intel: Unknown symbol snd_card_disconnect
[  975.364000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  975.364000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  975.364000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  975.364000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  975.364000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  975.364000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

Where do I go from here?  When I installed, it recognized an audio device, but even when I unmuted it, there would be no sound.  Now that I've tried all these fixes, alsa doesn't even think I have a soundcard anymore.  I'd rather not reinstall bc I've done so much work to get this set-up so far.  Please help!  Thanks!

---

### Post by aws910 on 2007-11-12
Did I post this in the wrong forum?  If so, which one should I have posted this in?  thanks.

---

### Post by veliro on 2007-11-12
Hope you posted it in the right forum. I am having the same problem,
Have worked on it for some days now, and nothing....

---

### Post by dabl on 2007-11-12
This is pretty good troubleshooting guidance for sound issues:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

:)

---

### Post by Pumalite on 2007-11-12
Try this:

sudo apt-get install linux-backports-modules-generic

---

### Post by aws910 on 2007-11-12
wow, well the backports thing restored my soundcard to "detected and installed", however...  no sound comes out still.  I guess this puts me back to square one(which is actually progress haha).  I'll retry the other articles and hopefully will come back with a "hda-intel success story"

---

### Post by Pumalite on 2007-11-12
What happens when you type this in the Terminal:

alsamixer

---

### Post by kylesykes on 2007-11-12
I am having the exact same problem as the OP.  I have tried all the guides, and no matter what i do i can't get my sound to work.  

When i run alsamixer, I get the bars showing Master, PCM, mic, mic boost, etc...

I have tried disabling the external amplifier, although i recently enabled it again as it did nothing.

I'm at a loss, the most current thing i've tried is
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
which sounded really promising, but didn't do any good that i can tell.

I'm pretty sure me and the original poster are in the EXACT same boat as we have the exact same laptop model and everything.

Misery loves company. :)

---

### Post by aws910 on 2007-11-15
Ah Kylesykes... we should start a support group haha

I tried that one too!  I thought it was funny that the "comprehensive sound problem guide" specifically said HDA-intel was hard to get working.

You know, now that I think of it, I do remember the sound tip at [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG) **worked** when I first tried edgy back in the day.... but now when I try it, I find that the "codepolice" patch link is broken. (the part that starts with "If you would rather not recompile ALSA yourself").  Now all I can find on the codepolice site is some business plan on making a boatload of money by selling gospel videos.  I think I've tried all the links from that page, but I'll keep trying.

If it wasn't for compiz, I'd be back to vista right now.... blasphemy, I know - its "Windows XP, Millennium Edition", but at least the soundcard works on it.

---

### Post by aws910 on 2007-11-15
got it working! :guitar: wow, only took me four months!  yeah enough of my whining, I know.  Here's how *I* did it:

(NOTE: I know this works with my Lenovo 3000 N100 0768 E7U, I'm not guaranteeing that it works with any other model/variant)

```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2
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
```
Reboot
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add this line at the end of the file:
```
options snd-hda-intel model=3stack
```
Save the file, close it, reboot, and CROSS YOUR FINGERS!

As usual, if there's no sound initially, open the volume control and make sure nothing is muted.  Also, open the volume control(doubleclick the speaker), click File->change device, select the OSS mixer, and make sure none of those output channels are muted either.  If none of these work for you, then you can try PM'ing me, but I'm pretty new to this still.

Much of this comes from the howto at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Note: Initially, because I had fiddled with it so much, I had nothing detected - a red X next to the volume control, would tell me I had no sound card when I tried to adjust volume.  To get rid of that, I ran "sudo apt-get install linux-backports-modules-generic" as suggested by Pumalite, and it restored it to (what appears to be) the default - sound card looks like it's working, but you can't hear sound out of anything.

Once again:  THANK YOU to everyone who helped me here!

---

### Post by kylesykes on 2007-11-15
I'll have to try this later tonight.

I hope to god it works...i think i did the same instructions you did, only i think i got the model wrong.  As we have the EXACT same laptop, i think i'll use the 3stack instead of the lenovo101 i used before.

If it works, i'll be thrilled.

---

### Post by kylesykes on 2007-11-15
It didn't work.  :(  I checked my volume settings under the GUI and under alsamixer, everything is turned on, and i tried it on multiple settings(the one you suggested and the other option it offered) and neither worked.

Here's the amixer output.

```
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 127
  Mono: Capture [off]
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 127
  Mono: Capture [off]
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 127
  Mono: Capture [on]
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 127
  Front Left: 127 [100%]
  Front Right: 127 [100%]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 127
  Mono: Capture [off]
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Mono',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 127
  Mono: Capture [off]
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 127
  Front Left: Capture 127 [100%] [0.00dB] [on]
  Front Right: Capture 127 [100%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Stereo Downmix',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

```

And here's another snippit of info from lspci -v

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 2066
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

I don't know what other info i can give.  I'd really appreciate some help with this if anyone can.

EDIT: I forgot to add this earlier...this is the error i get whenever i hit the "Test" button under System>Preferences>Sound.

[http://s205.photobucket.com/albums/bb21/kylesykes/?action=view&current=Screenshot-gnome-sound-properties-2.png](http://s205.photobucket.com/albums/bb21/kylesykes/?action=view&current=Screenshot-gnome-sound-properties-2.png)
[http://s205.photobucket.com/albums/bb21/kylesykes/?action=view&current=Screenshot-gnome-sound-properties-1.png](http://s205.photobucket.com/albums/bb21/kylesykes/?action=view&current=Screenshot-gnome-sound-properties-1.png)

hopefully that means something to someone.

---

### Post by aws910 on 2007-11-16
From your screenshots, you might have a problem with your GStreamer modules.  I don't know how safe it is(maybe someone else can clarify) but I'd just do a search on GStreamer in Synaptic, then try to remove/reinstall them.

---

### Post by Pumalite on 2007-11-16
I'd say he same; make sure you have all your GStreamers installed and working.

---

### Post by AddiKT1ve on 2007-11-16
Crap. I tried **everything** I could have seen in ubuntuforums, ubuntu-fr and others. My soundcard is HDA-Intel too, I compiled latest ALSA-something, I'm booting on a 2.6.22-14-generic kernel, model=auto or model=hp didn't work neither...

Now...

[IMG]http://www.thecheezburgerfactory.com//completestore/128374785565045000IMINURPUBDR.jpg[/IMG]

---

### Post by aws910 on 2007-11-17
addiktive, what model is your machine?  Maybe try the other options for the "model".  Sometimes the answer isn't always the most obvious :-/

Also, please post the output of the "aplay -l" and "sudo lspci -vv" commands

---

### Post by Ashrael on 2007-11-21
hmmm, i seem to have a similar problem :

[http://ubuntuforums.org/showthread.php?t=618554](http://ubuntuforums.org/showthread.php?t=618554)

But when i start up the livecd my soundcard works correctly???
Please try this...

thanx

---

### Post by spoonclaymore on 2007-11-21
aws910 -

Excellent work.  I have to admit that I feel like a bit of a slacker since you put all the hard work into this, but after wrestling with this for a day, your solution worked like a charm.

My situation happened when I upgraded from 7.04 to 7.10, and the first thing I had to deal with was the 640x480 resolution due to NVIDIA issues.  Once I got that figured out I had no audio, but your solution fixed it.

I am using a Dell Precision M65

Video = NVIDIA Quadro FX 350M
Audio = Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Also - /etc/modprobe.d/alsa-base works with this entry as well:

options snd-hda-intel model=auto

That was a residual from multiple other attempt to find a solution.

Thanks again for your good work.

---

### Post by spoonclaymore on 2007-11-23
Along with the above post my /etc/modprobe.d/alsa-base has this:

# autoloader aliases

install sound-slot-0 /sbin/modprobe snd-card-0

install sound-slot-1 /sbin/modprobe snd-card-1

install sound-slot-2 /sbin/modprobe snd-card-2

install sound-slot-3 /sbin/modprobe snd-card-3

install sound-slot-4 /sbin/modprobe snd-card-4

install sound-slot-5 /sbin/modprobe snd-card-5

install sound-slot-6 /sbin/modprobe snd-card-6

install sound-slot-7 /sbin/modprobe snd-card-7



# Cause optional modules to be loaded above generic modules

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }

install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }

install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }

install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }

# Cause optional modules to be loaded above sound card driver modules

install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }

install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }



# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)

install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }



# Load snd-seq for devices that don't have hardware midi;

#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for

#   non-Creative Labs PCI hardware

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }

# Prevent abnormal drivers from grabbing index 0

options snd-bt87x index=-2

options cx88-alsa index=-2

options saa7134-alsa index=-2

options snd-atiixp-modem index=-2

options snd-intel8x0m index=-2

options snd-via82xx-modem index=-2

options snd-usb-audio index=-2

options snd-usb-usx2y index=-2

options snd-usb-caiaq index=-2

# Ubuntu #62691, enable MPU for snd-cmipci

options snd-cmipci mpu_port=0x330 fm_port=0x388

options snd-hda-intel model=auto

#options snd-hda-intel model=3stack

---

### Post by aws910 on 2008-03-07
update:  wiped the machine and put kubuntu on, same problem on install.  This brought the sound back... updated for the new alsa version, and because I realized I used excessive sudo's in the first one.

```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2
tar xjf alsa-driver-1.0.16.tar.bz2
tar xjf alsa-lib-1.0.16.tar.bz2
tar xjf alsa-utils-1.0.16.tar.bz2
cd alsa-driver-1.0.16
./configure --with-cards=hda-intel
make
sudo make install
cd ../alsa-lib-1.0.16
./configure
make
sudo make install
cd ../alsa-utils-1.016
./configure
make
sudo make install
```

added to the end of /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=auto
```

I think "auto" is a little more friendly than "3stack", but ymmv... whatever works, you might have to try several of them.  Now I'm on to trying to figure out how to mute the front speakers when the headphones are plugged in!

---

