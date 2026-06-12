---
title: "Dapper to Edgy upgrade borked"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by steveneddy on 2006-10-29
I upgraded to Edgy, like everyone else, and now no nvidia driver works with Edgy. I only get GUI with the vesa driver.

I upgraded using the "update-manager -c" method. It upgraded fine. No probs, really. But the graphical interface sucks. I can only use the "vesa" driver.

I am using the "generic" linux kernel and the "nvidia-glx" driver.

When I use the "nv" driver, it almost logs on completely, I can see the boot splash, the icons start appearing in the Gnome bars, then it quits.

When I try to run the "nvidia" driver, nothing. X fails and keeps me in the CLI. 

I don't see a listing when running:
> 
cat /proc/driver/nvidia/version

when looking for the currently driver version.

Maybe that's where the problem lies. What do you think?

I just want my nice, pretty and fast GUI back so I can run beryl and watch videos. 

The windows I open up, when trying to scroll down the page, is very slow. I can actually see the page being drawn, the line goes down the page. Very annoying.

nVidia GeForce FX5200, PIII, Edgy, Fresh update to Edgy at that. 

Please help.

X doesn't work with the "UseFBDev" checked to "true".

Here's the important parts of my xorg.conf file:

> Section "Module"
        Load    "i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"nVidia"
	Driver		"vesa"
#	Option		"UseFBDev"		"true"
EndSection



I've been up literally all night reading the forums without an answer. Someone PLEASE help.

-SE

---

### Post by PizzAp on 2006-10-29
Hi,

1. Has the nvidia module been loaded without any problem? Check the output of the 'dmesg' command. Maybe with something like:
'dmesg | grep -2 NVIDIA'

1a. Read the output of 'lsmod' to check if the module has been loaded at all.

2. Look at the end of the Xserver log file '/var/log/Xorg.0.log'. Is there any error message?

3. If the Xserver starts, with nv for example, but the gnome session dies, check the output of '$HOME/.xsession-errors'

---

### Post by steveneddy on 2006-10-29
> **PizzAp said:**
> Hi,

1. Has the nvidia module been loaded without any problem? Check the output of the 'dmesg' command. Maybe with something like:
'dmesg | grep -2 NVIDIA'

No output in the terminal regarding this command

> 
1a. Read the output of 'lsmod' to check if the module has been loaded at all.

Here's the output of 'lsmod':

> 

Module                  Size  Used by
snd_rtctimer            4364  1 
binfmt_misc            13448  1 
rfcomm                 42260  0 
hidp                   34176  2 
l2cap                  27136  10 rfcomm,hidp
bluetooth              53476  5 rfcomm,hidp,l2cap
apm                    23280  1 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
ipv6                  272288  10 
dm_mod                 62872  5 
md_mod                 82836  0 
af_packet              24584  2 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                     12964  0 
rsrc_nonstatic         15360  0 
pcmcia_core            43924  1 rsrc_nonstatic
tulip                  54816  0 
tsdev                   9152  0 
serio_raw               8452  0 
evdev                  11392  1 
analog                 12960  0 
snd_mpu401_uart        10240  0 
floppy                 63044  0 
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
gameport               17160  1 analog
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
hw_random               7320  0 
psmouse                41352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
pcspkr                  4352  0 
snd_intel8x0           34844  3 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_rtctimer,snd_seq,snd_pcm
snd                    58372  16 snd_seq_oss,snd_seq,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              26012  1 
agpgart                34888  1 intel_agp
i2c_i810                6276  0 
i2c_algo_bit           10376  1 i2c_i810
i2c_core               23424  1 i2c_algo_bit
ext3                  142728  2 
jbd                    62228  1 ext3
usbhid                 45152  0 
ohci1394               37040  0 
ieee1394              306104  1 ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_disk               18560  5 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
piix                   11780  1 
generic                 5764  0 
processor              31560  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability



> 
2. Look at the end of the Xserver log file '/var/log/Xorg.0.log'. Is there any error message?


No error messages using the 'vesa' driver. 

> 
3. If the Xserver starts, with nv for example, but the gnome session dies, check the output of '$HOME/.xsession-errors'

Here is the contents (the last third) from /.xsession-errors:

> 
(update-notifier:4938): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible

(gnome-power-manager:4933): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized
GTK Accessibility Module initialized

(evolution-alarm-notify:4941): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
evolution-alarm-notify-Message: Setting timeout for 42047 1162188000 1162145953
evolution-alarm-notify-Message:  Mon Oct 30 00:00:00 2006

evolution-alarm-notify-Message:  Sun Oct 29 12:19:13 2006

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
GTK Accessibility Module initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized

(gnome-terminal:5132): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(nautilus:5161): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(gedit:5196): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(gedit:5202): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(gedit:5206): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(nautilus:5210): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(gedit:5233): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible


I researched the 'libgail-gnome' module, but didn't see it in the repositories and it looked like a dimished file with gnome.

I hope that you can help me.

-SE

---

### Post by PizzAp on 2006-10-29
The libgail-gnome messages are just warnings. I can't tell why your gnome-session dies.

Probably you should fix the display driver first.

I'll assume you want to install the nvidia driver. You first need to load the kernel module, than reconfigure your Xserver to  use the 'nvidia' driver.

Try a 'modprobe nvidia' if that works (see dmesg/lsmod) you should make certain it gets loaded at boot time: 
```
echo "nvidia" >> /etc/modules
```


If your gnome-session keeps dying you could try to add a new user, 'adduser test', and check if he can log in.
If not it is something with your system, if the test user can log in than something is wrong with your gnome profile.

Hope this gets you somewhere...

---

### Post by steveneddy on 2006-10-29
> **PizzAp said:**
> The libgail-gnome messages are just warnings. I can't tell why your gnome-session dies.

Probably you should fix the display driver first.

I'll assume you want to install the nvidia driver. You first need to load the kernel module, than reconfigure your Xserver to  use the 'nvidia' driver.

Try a 'modprobe nvidia' if that works (see dmesg/lsmod) you should make certain it gets loaded at boot time: 
```
echo "nvidia" >> /etc/modules
```


If your gnome-session keeps dying you could try to add a new user, 'adduser test', and check if he can log in.
If not it is something with your system, if the test user can log in than something is wrong with your gnome profile.

Hope this gets you somewhere...

I gave up and reinstalled, which is probably as much work as trying to get Edgy running. I'm normally not a quiter, but I have to go to work on Monday AM and I need to come home and do work, also. I used bad judgement by taking a system that was working perfectly with the Nvidia Beta driver and beryl and borked things up beyond repair. 

I think I learned my lesson. 

I installed Firefox 2.0 and am trying to remember what I did to customize my system before, like the icon themes, the window borders and the wallpapers. I did save the pics and wallpapers on the other HD, so everything wasn't lost. 

I don't think that Edgy is ready for everyone. I think I'll try the LiveCD first next time. 

Thanks for the help. I appreciate your time.

-SE

---

### Post by PizzAp on 2006-10-30
Ah well, doesn't sound too bad, if you only lose desktop settings it is probably faster to reinstall.
I've got 3500 packages installed, a fresh install would take me ages. Luckily upgrading to edgy worked quite well for me.

I guess dapper still is the 'stable' ubuntu... ;)

---

