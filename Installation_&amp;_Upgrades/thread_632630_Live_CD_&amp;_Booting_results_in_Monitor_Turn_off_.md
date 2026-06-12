---
title: "Live CD &amp; Booting results in Monitor Turn off - Cannot Use Ubuntu"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by dancecharlie on 2007-12-05
Dear Ubuntu community,

Recently I downloaded the Live CD 7.10 (md5 check was ok) and booted into it. It came up with the boot menu with options to run the Live CD - do a memory test, check the CD for defects etc - as normal. When selecting to run the Live CD (or any of the options except for the memory test, which seemed to work), a loading bar appears and loads the Linux Kernal. It completes the loading and then displays a black screen with white writing (like dos). The weird thing is, is that this writing is cut off on all sides as if it is displaying at a resolution higher than what the monitor can show. Very quickly it then turns off the monitor (puts it into standby) and my keyboard's lights (capslock etc) start flashing.

I have tried leaving it in this state to see if it would get passed it. It doesn't. The only thing to do at this point it to restart the computer with the restart button the computer.

I have tried using the text mode on the Live CD and booting with the added vsync= command. It doesn't work.

I have tried using another monitor (listed below), but it doesn't work.

I then decided that perhaps it was the Live CD, so I downloaded the Alternate CD. With this CD I was able to install Ubuntu. Now when I try to boot into Ubuntu from the GRUB loader, I have the same problem as with the Live CD.

I have tried 'sudo dpkg-reconfigure xserver-xorg' in recovery mode, and configured the monitor's resolutions correctly (One note here - There are no instructions that describe which keys to use to select the resolutions for xserver to use. I eventually found out that it was spacebar to select).  I have also configured the vertical and horizontal frequencies through the advanced setup, but still when booting into Ubuntu, the monitor goes into standby and nothing happens.

I can however boot into recovery mode and use 'startx' to start the xserver, and Ubuntu works fine. From here I tried changing the screen settings through the Screen and Graphics program. One odd thing is that It defaults to thinking that my monitor is an LCD 1024x768 (my specs below). I can change it to Monitor 1600x1200, but it still doesn't detect the proper resolutions the monitor can show.

I have tried this method described here, thinking this could be the problem: [http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

This however didn't work either, so I don't know what to do. I'm new to Linux and Ubuntu (though tried Ubuntu 6.10 edgy eft on this same computer, and it worked fine - another weird thing. It must be something different with 7.10).

I would really like to solve this problem as I really want to get to learn Linux and Ubuntu. Here is my computer setup:

AOC 9klr monitor (my default monitor)
Philips 107S5 monitor (second monitor I tried)

Giga-Byte K8NSNXP nforce3 based Motherboard
AMD Athlon 64 +3200 - 2.21GHz
1.0 GB ram (2x512)
Ati Radeon X800 XT graphics card
Creative Audigy 2 ZS sound card

120GB Seagate Sata I HDD, Formatted like this:

84 GB - WinXP Pro NTFS
14 GB - Ubuntu Ext3
2.0 GB - Swap
20 GB - Fat32 (to share between Ubuntu and WinXp)

If there is any other information that would help, I can provide it.

Thanks in advance,
-dancecharlie

---

### Post by Pumalite on 2007-12-05
Summary
The AOC 9KLR means business. With an impressive 18” flat face surface that eliminates glare, this display is the definition of precision. If you’re a dedicated graphics or multimedia artist, the AOC 9KLR will revolutionize your view of design.

Features

    * Display Size: 19" (18" Viewable)
    * Resolution: 1160 x 1200 (Maximum)
    * Pixel Pitch: 0.21mm 

    * Connectivity: 15-pin D-Sub (Analog)
    * Cabinet Color(s): White
    * Environments: PC and Mac 

Have you tried a more 'run of the mill' CRT?

---

### Post by dancecharlie on 2007-12-05
Yes, I tried a Philips 107S5, and it didn't work either. My AOC 9KLR worked fine with Ubuntu 6.10 though, which is odd.

Thank you for your quick reply

Do you think it is a monitor problem? Does the new Ubuntu just not support it?

---

### Post by Pumalite on 2007-12-05
Take a look at this:
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=579881](http://ubuntuforums.org/showthread.php?t=579881)
[http://ubuntuforums.org/showthread.php?t=505249](http://ubuntuforums.org/showthread.php?t=505249)
[http://ubuntuforums.org/showthread.php?t=601775](http://ubuntuforums.org/showthread.php?t=601775)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html](http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html)

[http://ubuntuforums.org/showpost.php?p=3484653&postcount=15](http://ubuntuforums.org/showpost.php?p=3484653&postcount=15)

Hopefully you'll find your answer here.

---

### Post by nzadLithium on 2007-12-05
I think whats happening is the driver the x server is using for your graphics card is wrong.
can you boot into text mode (the second boot option) and then login. 

if you havent setup a root password then type sudo passwd (i think thats write command)
set it up. make sure you remember that password. Its the administration one.

To install driver from repository type: 
> sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

if you want to install the latest drivers from ati (i doubt the ubuntu ones are up to date probably one version number behind)
run:
wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run)

this will download the latest driver 
then follow this to install it: 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)
when it says gksu gedit you will have to replace it with sudo nano because the other one needs the gui.

to use the nano program the commands are written down the bottom. This ^ means ctrl + the key it says.

---

### Post by dancecharlie on 2007-12-05
I will try this method now and report back.

Thanks for the other links too.

---

### Post by dancecharlie on 2007-12-05
I tried the method mentioned but it stated that it was already the latest version. I will try installing the Ati made drivers soon and report back again.

Note that I can get into Ubuntu through using 'startx' in recovery mode, and the appearance is fine. It's just booting into Ubuntu (non-recovery mode) where it turns the monitor off and doesn't do anything. If I can get passed that, I'm presuming Ubuntu will work as it does if i use 'startx' in recovery mode.

---

### Post by nzadLithium on 2007-12-05
ok well if thats the case dont bother installing the ati drivers yet.

start up in recovery mode and run startx then type lsmod into a terminal post output here
then gksudo gedit /etc/X11/xorg.conf and post here as well. I gona check if its loading different drivers.

---

### Post by dancecharlie on 2007-12-06
xorg:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R420 JP [Radeon X800XT]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"AOC 9klr"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JP [Radeon X800XT]"
	Monitor		"AOC 9klr"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1440x900" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Typing in 'ismod' gives, "bash: ismod: command not found"

I didn't know what this was, so I searched it and decided to type in this:

'insmod' returns, "Usage: insmod filename [args]"

Thanks for your help.

---

### Post by nzadLithium on 2007-12-06
ill spell it out in caps just be sure to make it little letters when you run it LSMOD
it seems the driver that the x server is trying to use is 'ati' this could be a problem because as far as i know the ati driver only supports ati radeon cards its supposed to be the R100 and R200 chipsets?

so run lsmod and we'll see what its loading that does get your xserver up. make sure you startx before you run it.

---

### Post by dancecharlie on 2007-12-06
lsmod:

```
root@mehubuntu:~# lsmod
Module                  Size  Used by
radeon                129824  0 
drm                   106408  1 radeon
nls_iso8859_1           6528  1 
nls_cp437               8192  1 
vfat                   16128  1 
fat                    60208  1 vfat
sbp2                   27144  0 
lp                     15048  0 
loop                   21764  0 
snd_emu10k1_synth       9344  0 
snd_emux_synth         40064  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_emu10k1           152864  2 snd_emu10k1_synth
snd_ac97_codec        122200  1 snd_emu10k1
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         12560  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9984  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                62496  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
emu10k1_gp              5632  0 
parport_pc             41896  1 
analog                 13408  0 
gameport               18704  3 emu10k1_gp,analog
pcspkr                  4608  0 
parport                44172  2 lp,parport_pc
k8temp                  7680  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
i2c_nforce2             7808  0 
i2c_core               30208  1 i2c_nforce2
ipv6                  317192  8 
evdev                  13056  0 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  5 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
sata_nv                24068  4 
usbhid                 32576  0 
hid                    33408  1 usbhid
floppy                 69608  0 
sata_sil               14600  0 
skge                   47248  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ata_generic             9988  0 
libata                138928  3 sata_nv,sata_sil,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
forcedeth              55048  0 
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  4 usbhid,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  1 thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor
```

---

### Post by dancecharlie on 2007-12-06
Well I decided to go back to edgy eft as I needed to get some work finished today, and everything is running fine. Thank you all for your help though, especially you nzadLithium. Thank you.

I'm guessing the problem came down to Ati drivers, and for some reason the drivers in edgy eft work for my card, while the drivers in gusty gibon don't so well.

Again, Thank you.



Have a great day

---

### Post by nzadLithium on 2007-12-08
i'm not sure but its a possibilty that your card needs to use the 'radeon' driver and although the 'ati' driver should find the right modules it could be using some other open source module that isnt working. It may have worked if you changed in your xorg.conf the line that says driver "ati" to driver "radeon"

---

### Post by gonesolo on 2007-12-14
Bit late now but if you ever try to install 7.10 again try this.

Install using the alternative CD 

When Ubuntu boots - select recovery mode.

edit the GRUB.LST file and remove "SPLASH" from the end of the line that boots Ubuntu normally.

This resolved the issue for me. 


(now if I could just get my X-FI to work :()

---

