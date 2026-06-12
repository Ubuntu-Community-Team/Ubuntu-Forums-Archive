---
title: "Up graded from 10.04 to 12.04 no wireless"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by cranecreek on 2012-09-07
I recently up graded from ubuntu 10.04 to 12.04 and now my wireless doesn't work
lspci -nn```
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```b43 is installed when I try airmon-ng no interface shows up.
This seems like a driver issue, has anyone solved this problem.

Also during the 4 hour upgrade a package was broken, it was dell power dvd(pdvdlinux) It errors out and doesn't let me install new programs such as compiz manager.```
Do you want to continue [Y/n]? y
(Reading database ... 560370 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux

```  Additional info:
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux

```lspci -nnk | grep -iA2 net
```
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Dell Device [1028:0271]
    Kernel driver in use: forcedeth
--
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel modules: ssb

```lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63fa Microdia 
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth

```rfkill list all
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod
```
Module                  Size  Used by
dm_crypt               22528  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
nvidia              10962290  43 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               67203  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25424  1 snd_seq_midi
ir_lirc_codec          12739  0 
snd_seq_midi_event     14475  1 snd_seq_midi
lirc_dev               18700  1 ir_lirc_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_mce_kbd_decoder     12681  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_sony_decoder        12462  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
ir_jvc_decoder         12459  0 
bch                    21757  1 nand_bch
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
dell_wmi               12601  0 
rc_rc6_mce             12454  0 
sparse_keymap          13658  1 dell_wmi
ir_nec_decoder         12459  0 
psmouse                72919  0 
mxm_wmi                12859  0 
dell_laptop            17767  0 
ite_cir                24743  0 
dcdbas                 14098  1 dell_laptop
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
r592                   17808  0 
shpchp                 32325  0 
nand_ecc               13070  1 nand
serio_raw              13027  0 
memstick               15857  1 r592
wmi                    18744  2 dell_wmi,mxm_wmi
mac_hid                13077  0 
soundcore              14635  1 snd
i2c_nforce2            12906  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
firewire_sbp2          18346  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
firewire_ohci          40172  0 
firewire_core          56906  2 firewire_sbp2,firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
forcedeth              58096  0 
video                  19068  0 

```Any suggestions would be appreciated.

---

### Post by cranecreek on 2012-09-08
Ubuntu released an up date which was kernel update with a partial upgrade in my case.

Check for updates.
Install.
Click the network manager icon.
Enable wireless.
Then wait, and at least I am good to go.


Hope this helps someone else.

---

### Post by randrews on 2012-09-08
I have the same card, and moved up from 10.04 to 12.04 a week or so back. But I didn't attempt to upgrade from one version to the other. I just backed up my home directory, burned an .iso to disc, and booted to it for the install.

The install went quite painlessly, and the installation routine showed my wireless card working fine before it began the actual install. But I have no idea if this was because the card was already working on the previous version, or if the installer came up in some sort of live mode and pre-configured it.

Did you try a direct upgrade, or a wipe & reinstall?

---

### Post by mikewhatever on 2012-09-08
While b43 may be installed, the module is definitely not loaded. Double check that it is installed, then try loading it with 

sudo modprobe b43

If that works, add b43 to /etc/modules to make sure it autoloads.

As for pdvdlinux, try renaming its post-removal script (it's probably safe to remove it right away, but that can be done later):

sudo mv /var/lib/dpkg/info/pdvdlinux.postrm /var/lib/dpkg/info/pdvdlinux.postrm-renamed

...and then

sudo apt-get purge pdvdlinux

---

