---
title: "Install from USB onto EEE PC"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by charlieholder on 2010-04-20
Hello all.

Recently upgraded my ASUS EEE PC 900A. Gave it a tune up with a new 32GB Patriot Lite SSD drive and a 2GB Kingston RAM chip. I also put the latest copy of Ubuntu 9.10 on it via USB. Can't connect to my wireless network and don't know why. I've added the network to the list of connections.

Found this post ([http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)) and it seems to be somewhat similar to the issues I am having. I don't really know much about the types of solutions that the different people offered. I am having a little bit of difficulty understanding exactly what I need to do in order to be able to use my wireless capabilities. I am quite lost when it comes to "installing deb files" and reading about "dependencies."

Before I upgraded the EEE PC, it had a copy of GNU Linux preinstalled on it. I know it can connect to wireless because I set it up on that. I don't know what kind of card it has. I'll try to look around and figure out if I can find where it might tell me. Otherwise I might need help in that area too.

Thanks for any help you can offer.

---

### Post by tommcd on 2010-04-20
From some quick googling it seems that there is some difficulty with the wireless key on the keyboard of the 900a.See this:
[http://ubuntuforums.org/showthread.php?t=1415671](http://ubuntuforums.org/showthread.php?t=1415671)
If your wireless is not working, then reboot the system. Hopefully this should re-enable the wireless as it says in that thread.
The 900a is listed as a "tier 1" netbook in the Ubuntu wiki. It is reported that everything works:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20900a](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20900a)
Also, to make it easier for you to connect to wireless networks, I would recommend that you install **wicd**. Wicd is an easy to use graphical program for finding and connecting to wireless networks. (Note that installing wicd will remove Ubuntu's network-manager. This is not a problem though).
If you don't know how to install software in Ubuntu, see these:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
You will need to get online with the wired ethernet on the 900a to install wicd and get the updates for Ubuntu.

Just to make sure that the wireless card on the 900a is detected and the proper drivers are loaded for it, run these 2 commands from the terminal (applications > accessories > terminal):
The first command is **lspci**. This will list all your hardware devices, including the wireless. The wireless card will be near the end of the output for lspci.
The second command is **lsmod**. This will list all of the drivers currently loaded on your system. Post the output of lspci and lsmod here.

And welcome to the Ubuntu forums!

---

### Post by charlieholder on 2010-04-22
Thanks for the help tommcd.

I was able to get the first issue with the wireless working.

I'll be trying to tackle the wicd install this weekend.

---

### Post by charlieholder on 2010-04-22
Also, here's the output for those two commands. It's kind of long and the tabbing for the lsmod is TERRIBLE.

lspci
> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

lsmod
> Module                  Size  Used by
aes_i586                8124  2

aes_generic            27484  1 aes_i586

binfmt_misc             8356  1

ppdev                   6688  0

arc4                    1660  2

joydev                 10272  0

ecb                     2524  2

snd_hda_codec_realtek   203328  1

snd_hda_intel          26920  2

snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel

snd_hwdep               7200  1 snd_hda_codec

snd_pcm_oss            37920  0

snd_mixer_oss          16028  1 snd_pcm_oss

snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss

iptable_filter          3100  0

ip_tables              11692  1 iptable_filter

snd_seq_dummy           2656  0

x_tables               16544  1 ip_tables

snd_seq_oss            28576  0

snd_seq_midi            6432  0

snd_rawmidi            22208  1 snd_seq_midi

ath5k                 124260  0

snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi

mac80211              181236  1 ath5k

snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

led_class               4096  1 ath5k

ath                     8060  1 ath5k

snd_timer              22276  2 snd_pcm,snd_seq

snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

eeepc_laptop           13936  0

lp                      8964  0

parport                35340  2 ppdev,lp

cfg80211               93052  3 ath5k,mac80211,ath

psmouse                56180  0

serio_raw               5280  0

soundcore               7264  1 snd

snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

fbcon                  36640  72

tileblit                2460  1 fbcon

font                    8124  1 fbcon

bitblit                 5372  1 fbcon

softcursor              1756  1 bitblit

atl1e                  31824  0

i915                  221064  3

drm                   159584  3 i915

i2c_algo_bit            5760  1 i915

intel_agp              27484  2 i915

agpgart                34988  2 drm,intel_agp

video                  19380  1 i915

output                  2780  1 video

---

### Post by tommcd on 2010-04-23
> **charlieholder said:**
> 
I was able to get the first issue with the wireless working.
I'll be trying to tackle the wicd install this weekend.
So your wireless in now working ok then?
Your lspci output indicates that your wireless card is an Atheros Communications Inc. AR5001. And your lsmod indicates that the ath5k driver is loaded, which should be the correct driver for your wireless card. 
If your wireless is working ok, then you don't need to install wicd. I personally like wicd more than Ubuntu's network manager. It is your call though.

---

### Post by charlieholder on 2010-04-23
> **charlieholder said:**
> I was able to get the first issue with the wireless working.

I was, yes. THanks.

---

