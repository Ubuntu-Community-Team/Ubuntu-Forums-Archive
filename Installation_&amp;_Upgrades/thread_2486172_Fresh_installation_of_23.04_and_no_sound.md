---
title: "Fresh installation of 23.04 and no sound"
date: 2023-04-21
forum: Installation &amp; Upgrades
---

### Post by eriolbrumel on 2023-04-21
Hi,

after several rounds of upgrades I decided this time to do a clean install of the OS on my HP notebook. Most things work out of the box as usual, but I have no sound. If I play audio it shows that something is playing, but I do not hear anything from the speakers.

Connecting bluetooth headphones works, and audio plays. Can someone help, please? I am not getting further ...

 Here is some output:

```

[FONT=monospace][COLOR=#54FF54]**eriol@Messiah**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ cat /proc/asound/cards  [/COLOR]
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa4228000 irq 131
[/FONT][FONT=monospace][COLOR=#54FF54]**eriol@Messiah**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ aplay /usr/share/sounds/alsa/Front_Center.wav  [/COLOR]
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
[/FONT][FONT=monospace][COLOR=#54FF54]**eriol@Messiah**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lsusb[/COLOR]
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. Realtek Bluetooth 4.2 Adapter
Bus 001 Device 003: ID 0408:5300 Quanta Computer, Inc. HP Wide Vision HD Camera
Bus 001 Device 002: ID 03f0:3b41 HP, Inc OMEN Vector Mouse     
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=#54FF54]**eriol@Messiah**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lspci[/COLOR]
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point LPC Controller/eSPI Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce MX130] (rev a2)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
[COLOR=#54FF54]**eriol@Messiah**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]
```

---

### Post by idmbe on 2023-04-23
Hello [[COLOR=#000000]eriolbrumel[/COLOR]]("https://ubuntuforums.org/member.php?u=2075229"), 

Check that link:
[URL="https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en"]https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en
[/URL]hope will be helpful for you

---

### Post by arcxjo2 on 2023-06-21
There is not a shred of actual help in that file.

---

### Post by utnubuPete on 2023-12-14
I had a similar problem having upgraded to 22.04.  Bluetooth was very un-reliable and mostly did not work and the sound from speakers was not reliable.  So I investigated pipewire and bluealsa and then ended up back with pulseaudio.  Now my bluetooth is reliable.  My conclusion is that you can not mix bluealsa and pulseaudio.  Reading this - [https://github.com/arkq/bluez-alsa/wiki/PulseAudio-integration](https://github.com/arkq/bluez-alsa/wiki/PulseAudio-integration) was very useful and helped get rid of all the bluealsa bits that were getting in the way of pulseaudio.  [https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/) was also useful for removing pipewire.

So to troubleshoot I use pavucontrol (works with both pulseaudio and pipewire) and audacity - because it has good debug logs and helpful information about what audio drivers it can see.  Typically problems are fixed by "sudo alsa force-reload" or / and pulseaudio -k and sometimes alsactl kill quit and alsactl init.  Worst case I simply logout and back in again.  Then after configuring with pavucontrol or pactl - bluetooth is working.

Once audacity is working I start qjackctl with the configuration from [https://askubuntu.com/questions/572120/how-to-use-jack-and-pulseaudio-alsa-at-the-same-time-on-the-same-audio-device](https://askubuntu.com/questions/572120/how-to-use-jack-and-pulseaudio-alsa-at-the-same-time-on-the-same-audio-device) so that when I close JACK I can get back to pulseaudio.  With JACK running I use "pactl load-module module-loopback" and connect my source up to PulseAudio JACK Source in  qjackctl "graph" view - [https://unix.stackexchange.com/questions/465703/using-a-bluetooth-speaker-as-output-for-jack-audio-connection-kit](https://unix.stackexchange.com/questions/465703/using-a-bluetooth-speaker-as-output-for-jack-audio-connection-kit)

So in summary if I am not using JACK then I can hear audio via pulseaudio, selecting the profile and headphones via pavucontrol or via a script using pactl set_profile... and pactl set_default_sink... and then if I want to use the keyboard or other audio application via JACK I used pulseaudio loopback module.

pulseaudio - I have a2dp-sink profile and handsfree hfp-ag working.
bluealsa - I built from source and got very reliable results but only the handsfree profile recognised and could not start a2dp-sink.
pipewire - I used the stock Ubuntu 22.04 code but gave up trying to get audio or bluetooth running.  I suspect that this was largely caused by multiple configuration files in /etc/alsa/conf.d that pipewire does not seem to like.. apparently removing all of them apart from what pipewire needs is a good idea.. they are all symbolic links after all and can easily be configured if you go back to pulseaudio.  [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976309](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976309)

---

### Post by SeijiSensei on 2023-12-15
Since you have the NVIDIA driver installed, it's possible the sound is being routed to the HDMI port rather than the speakers. Install pavucontrol if you don't have it, and see how many audio devices it finds and which is the default.

---

### Post by MAFoElffen on 2023-12-17
Hmmm. Fresh install of Lunar 23.04.

23.04 losses support next month (in January)... When you get it working, you might think about upgrading the release so you don't get behind with that. Just a thought. Get good backups.

---

