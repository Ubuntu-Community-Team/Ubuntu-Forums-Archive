---
title: "speaker only creates static instead of sound"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by skarosg3 on 2013-05-23
Hi all,
I just upgraded to 13.04 and i got a problem with my audio.

I am only getting static noise instead of any sound from the speaker. I have tried a dozen different things, but nothing worked. 

i am not sure what might be useful for you guys, so i am going to paste here a number of different commands in case they help.
```
[SIZE=2]
ilias@ilias-System-Product-Name:~$ ps -ef|grep pulseaudio
ilias     1701     1  0 23:24 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
ilias     1868  1701  0 23:24 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
ilias     2570  2410  0 23:27 pts/0    00:00:00 grep --color=auto pulseaudio

ilias@ilias-System-Product-Name:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 19
 1 [Device         ]: USB-Audio - PnP Audio Device
                      PnP Audio Device at usb-0000:00:02.0-7, full speed

ilias@ilias-System-Product-Name:~$ ps -ef|grep alsa
ilias     2577  2410  0 23:28 pts/0    00:00:00 grep --color=auto alsa

ilias@ilias-System-Product-Name:~$ less /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio[/SIZE]
```
i tried disabling these two one at a time, but when i disabled the hda_intel nothing changed, and when i disabled the usb_audio there was no sound at all, not even the noise. like it was mutted.

when i enter alsamixer i am getting these 2 cards:
HDA NVIDIA
PnP Audio Device.

i hope all these information help. thanks in advanced,ilias

---

### Post by skarosg3 on 2013-05-24
no one?
any ideas?
nothing?
:(

I am pretty sure i didnt discard the files after the update. is there a way to go back to that configuration, since it was working?

---

