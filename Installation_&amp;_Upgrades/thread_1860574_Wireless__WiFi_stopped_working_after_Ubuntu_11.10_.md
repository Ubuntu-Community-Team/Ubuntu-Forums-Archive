---
title: "Wireless / WiFi stopped working after Ubuntu 11.10 upgrade"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by cirelosborn on 2011-10-14
I hope this helps someone out there, here's my story and how I fixed it.

After I upgrade from 11.04 to 11.10 my WiFi went out during installation and never came back on, even after the install completed.  My netbook is a Sony VAIO VPCM111AX, I was familiar with the the ralink wireless issues so I had many rt2 and rt3 wireless drivers blacklisted.  So I went back and unblacklisted these drivers.

```
sudo gedit /etc/modprobe.d/blacklist.conf
```
> # These don't function with WiFi when netbook is unplugged
blacklist rt3390sta
blacklist rt2x00lib
blacklist rt2800pci
blacklist rt2x00usb
blacklist rt2x00pci

This didn't solve the problem.  I went back to find my specific driver by this:

```
lspci | grep work
```

and I found that my driver was RT3090

> 01:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

Upon some investigation I found that 11.10 doesn't support some wireless drivers.
Before proceeding I wanted to check a few more things such as

```
sudo lshw -C network
``` 
> *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 0c:ee:e6:ff:17:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 ip=192.168.2.10 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 02
       serial: 00:24:be:c4:d4:85
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 memory:fe800000-fe803fff ioport:e100(size=128) ioport:e000(size=256)

Then:

```
lsmod
```
> Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
mmc_block              22393  1 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
btusb                  18160  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_realtek   254125  1 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                73673  0 
serio_raw              12990  0 
rt3090sta             794403  1 
drm_kms_helper         32889  1 i915
sony_laptop            39681  0 
drm                   192226  4 i915,drm_kms_helper
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
jme                    40330  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci


Lastly I checked this: 

```
rfkill list all
```
> 0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


If the "no"'s here are yes's for you run this:

```
rfkill unblock all
```

After all this I found an old version of the rt3090 driver here: 

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb")

I installed the driver and restarted the computer and all is well.  I haven't had to reblacklist the other ralink drivers, everything seems to be working well.

I hope this helps someone because this problem drove me mad.

Just for reference:  I did find that some computers needed to blacklist certain drivers depending on computer models:

> blacklist bcm43xx
blacklist acer_wmi 

There are a lot of other drivers that need to be blacklisted depending on the type of computer you have and others need to install older versions of the wireless driver (as I did) to allow this to work.

---

### Post by dfv78 on 2011-10-15
Thank you!

It worked as you said on my HP ProBook 4720s.

- I removed the blacklist rt2800pci (I had blacklisted this one when I upgraded to 11.04). This restored the ability to activate the wireless network using the wireless button. But I still couldn't connect to any Access Point.

- I installed the old driver using the link you provided. 

- and I blacklisted bcm43xx and acer_wmi just in case.

Thanks again :)

---

### Post by cu_ on 2011-10-15
Thanks OP.  This definitely helped me.  On my averatec N1200, it first gave me a warning that the "driver does not meet ubuntu standards" which I ignored.  After reboot, it "forgot" my wpa-2 password. I had to retype it.  Everything works now.

If anyone is looking for instructions....  all it needs it download and install deb file linked by OP using the software center.  The install can take a while because it is DKMS, be patient.

---

### Post by Pro$pect on 2011-10-15
life saver!!! been messing with this for days

---

### Post by kpuz on 2011-10-16
Thank you very much for this information. About to go try it out.

---

### Post by papahippo on 2011-10-18
I'm another satisfied customer; thanks!:)

on the downside...
8-[
I was rather worried at having to scorn two security warning in order to install the good old driver.  This might encourage me  to adopt such pig-headed behaviour at less appropriate times.

My confidence as a self-styled "Ubuntu evangelist" takes a knock when I hit this sort of problem.

---

### Post by Hrairoo on 2011-10-19
Worked for me, I just had to add a line to the /etc/modules

rt3090sta

and after a reboot. Everything worked ok. :)

---

### Post by dipta on 2011-10-21
Thank you guys, especially to [cirelosborn]("http://ubuntuforums.org/member.php?u=1221533")
It works very well.
I should see this thread when i just upgrade to 11.10 soon !

---

### Post by moteprime on 2011-10-25
Hi, I have a Lenovo s205, and have been struggling really hard to get wireless working right.
I can get it to works in several different ways, but the network speed is very low.
Now I have downloaded the package "rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb" from Markus Heberling, and installed it using software center.
It did not work, so I blacklisted "acer_wmi", and now it does. -But again at a terrible  low speed. (below 80Kb/sec.)
How do I find out what drivers should be blacklisted, and what driver is actually being used?

---

### Post by moteprime on 2011-10-25
I've been fighting this for 3 weeks straight, but now it finally works.
cirelosborn you are a true hero!

What it took was to install version 2.3.1.3 (I had installed 2.4.0.4)
Blacklist acer_wmi in /etc/modprobe.d/blacklist.conf
And add rt3090sta to /etc/modules

---

### Post by siddi on 2011-11-20
How about an Acer Aspire 5570.... Is it the same procedure?

---

### Post by siddi on 2011-11-20
> **cirelosborn said:**
> I hope this helps someone out there, here's my story and how I fixed it.

After I upgrade from 11.04 to 11.10 my WiFi went out during installation and never came back on, even after the install completed.  My netbook is a Sony VAIO VPCM111AX, I was familiar with the the ralink wireless issues so I had many rt2 and rt3 wireless drivers blacklisted.  So I went back and unblacklisted these drivers.

```
sudo gedit /etc/modprobe.d/blacklist.conf
```
This didn't solve the problem.  I went back to find my specific driver by this:

```
lspci | grep work
```and I found that my driver was RT3090



Upon some investigation I found that 11.10 doesn't support some wireless drivers.
Before proceeding I wanted to check a few more things such as

```
sudo lshw -C network
```
Then:

```
lsmod
```
Lastly I checked this: 

```
rfkill list all
```
If the "no"'s here are yes's for you run this:

```
rfkill unblock all
```After all this I found an old version of the rt3090 driver here: 

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

I installed the driver and restarted the computer and all is well.  I haven't had to reblacklist the other ralink drivers, everything seems to be working well.

I hope this helps someone because this problem drove me mad.

Just for reference:  I did find that some computers needed to blacklist certain drivers depending on computer models:

 

There are a lot of other drivers that need to be blacklisted depending on the type of computer you have and others need to install older versions of the wireless driver (as I did) to allow this to work.






I got this after the lspci | grep work 
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
siddharth@siddharth-Aspire-5570:~$ sudo lshw -C network
[sudo] password for siddharth: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:8a:50:65
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:44000000-44003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:5d:03:ad
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:45 memory:44100000-44100fff
siddharth@siddharth-Aspire-5570:~$ 

Lsmod gave me this

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
gspca_vc032x           31999  0 
gspca_main             27610  1 gspca_vc032x
videodev               85626  1 gspca_main
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
pcmcia                 39822  0 
snd_hda_intel          24262  5 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
tifm_7xx1              12937  0 
bluetooth             148839  23 bnep,rfcomm,btusb
tifm_core              15040  1 tifm_7xx1
yenta_socket           27428  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
iwl3945                73329  0 
i915                  505108  3 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
snd                    55902  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
wmi                    18744  1 acer_wmi
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 

And after the rfkill comand.... All the answers are 'no'

What do i do?

---

### Post by cirelosborn on 2011-12-01
Intel Corporation PRO/Wireless 3945ABG is your wireless card.  If blacklisting didn't work then find an older version of the intel driver "3945ABG" and install it.  Hope this helps.

---

### Post by siddi on 2011-12-04
I haven't tried blacklisting cos am not sure what procedure i have to follow completely. 

Pls help

---

### Post by acme_labs on 2011-12-18
So here it is-  the HP dv5020us laptop, complete with non functioning wireless router, it does not even look for a driver! Help!
At my prompt,  I typed in this:

xxxx-Pavilion-dv5000-EP411UA-ABA:~$[COLOR=DarkRed] lspci | grep work[/COLOR]

and I got this

[COLOR=RoyalBlue]06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
[COLOR=Black]
What next?[/COLOR]
[/COLOR]

---

### Post by Cyberponcho on 2012-01-16
I wrote a little tutorial on this issue on my [blog]("http://cyberponcho.blogspot.com/2011/11/how-to-re-enable-wireless-in-ubuntu.html"), it did work perfectly well for me, maybe it can help someone here too :)

---

### Post by siddi on 2012-01-17
Mine says soft blocked no..... But still the wifi signal keeps dropping every few minutes.... sometimes every few seconds...

can there be a driver error?

---

### Post by shawnat88 on 2012-02-08
Worked perfectly on my mother's Compaq-Mini-CQ10-400. Thank you so much.

---

### Post by cirelosborn on 2012-02-09
The dropping of the wifi signal every few minutes is a classic sign of switching between two or more wireless drivers.  You need to blacklist all wifi drivers that your not using and it should stop dropping the signal.

---

### Post by borivoje on 2012-02-29
This really works. Thanks a lot!
Actually, Ubuntu 11.10 has no problem with the rt2860sta driver. It connects and works decently. But what I was doing is recompile the 3.0.0.16 kernel because I needed to patch it after buying Genius EasyPen i405X graphic tablet, which had pressure problem in the current kernel. I got pen to working but I lost connectivity with my rt3090sta wireless card.
Tried a lot of stuff but this solves the issue.

---

### Post by bikeman01 on 2012-03-16
I just reinstalled 11.10 (because I couldn't update 9.04!!)

I now have the same problem - no wireless.

I have consistently had problems with every single Ubuntu upgrade I have ever done. I'm not sure I even want to fix it this time...

---

### Post by jetblackstar on 2012-07-08
Another thanks and sucess to the OP.

Advent Milano netbook wireless on Ubuntu 12.04 working. thanks.
ALso thanks to the poster who suggested adding 
rt3090sta

to /etc/modules

Not 100% why that mod wouldnt already be set to load after installation but it got it working so thanks.

---

### Post by j26crowley on 2012-09-02
I registered so I could thank you OP
Spent hours on this and your instructions worked great.
:p

---

### Post by jcdispaux on 2012-09-03
Thanks a lot, Cirelosborn. My Acer AspireOne with Ubuntu 10.04 is working again. Promised: I will not upgrade again!:)

---

### Post by cirelosborn on 2012-10-18
After an upgrade to Ubuntu 12.04 I have found no problems with the wifi in any manner.

I've tested this with an HP laptop, HP Desktop, Sony netbook, Acer netbook, and a strange Chinese netbook named S30 (I have no idea what it really is).  Some of them had to be connected to an Ethernet cord for the clean install of 12.04.  After install I looked for "additional drivers", using Additional Drivers app pre-installed, and installed the wireless drivers for the ones that needed it (not all needed it).  That was it and everything worked beautifully.  So far, on the wireless aspect end of things, Ubuntu 12.04 beats Ubuntu 11.10 hands down.

Thank you everybody for the support.

---

