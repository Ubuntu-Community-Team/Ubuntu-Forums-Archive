---
title: "Karmic - some apps no sound"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by clickwir on 2009-10-10
Running Kubuntu 64 Karmic. As of yesterday, had sound working just fine in everything.

Today, I did an update and rebooted. Since then, sound in FLASH videos (such as YouTube) does not work. The video plays, but no sound. Same with VLC. However Kaffeine and Dragon Player both have sound. I used the same video for all 3. 

Amarok plays sounds just fine and the startup and shutdown sounds work fine.

So right now, Flash and VLC don't have sound. 

I just did an update and rebooted, but no difference. Here's some info that probably isn't relevant. 

```
clickwir@ruger10-22:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 LE [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
07:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
07:00.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
07:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
```

```
clickwir@ruger10-22:~$ uname -a
Linux ruger10-22 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:14 UTC 2009 x86_64 GNU/Linux

```

```
clickwir@ruger10-22:~$ aplay -l                                                                         
**** List of PLAYBACK Hardware Devices ****                                                             
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]                                              
  Subdevices: 1/1                                                                                       
  Subdevice #0: subdevice #0                                                                            
card 1: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]            
  Subdevices: 31/32                                                                                     
  Subdevice #0: subdevice #0                                                                            
  Subdevice #1: subdevice #1                                                                            
  Subdevice #2: subdevice #2                                                                            
  Subdevice #3: subdevice #3                                                                            
  Subdevice #4: subdevice #4                                                                            
  Subdevice #5: subdevice #5                                                                            
  Subdevice #6: subdevice #6                                                                            
  Subdevice #7: subdevice #7                                                                            
  Subdevice #8: subdevice #8                                                                            
  Subdevice #9: subdevice #9                                                                            
  Subdevice #10: subdevice #10                                                                          
  Subdevice #11: subdevice #11                                                                          
  Subdevice #12: subdevice #12                                                                          
  Subdevice #13: subdevice #13                                                                          
  Subdevice #14: subdevice #14                                                                          
  Subdevice #15: subdevice #15                                                                          
  Subdevice #16: subdevice #16                                                                          
  Subdevice #17: subdevice #17                                                                          
  Subdevice #18: subdevice #18                                                                          
  Subdevice #19: subdevice #19                                                                          
  Subdevice #20: subdevice #20                                                                          
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

***EDIT***
After much blah blah... running 'sudo apt-get install pulseaudio' fixed Flash sound and VLC sound. Both are working RIGHT NOW. YMMV. :-)

---

### Post by cucisan on 2009-10-12
same problem here.. no sound in songbird (from ppa) and flash..
i remember there was a pulseaudio update from 0.9.18 to 0.9.19..

i wonder if they ever will get this pulseaudio stuff working hasslefree.. 
i depend on it as i use airport streaming alot :)

---

### Post by geoffp on 2009-10-13
I have been seeing a behavior with MythTV, which I have set up to use the default ALSA device, wherein sound will intermittently die and won't work again until I kill pulseaudio and relauch it from the command line.

Since my upgrade to Karmic, all my emulators also emit no sound at all.  I believe those, too, are using ALSA.

Might this be an issue with PA's virtualization of the ALSA api, I wonder?  Is anyone else seeing this kind of thing?

---

### Post by clickwir on 2009-10-14
FYI, still same issue after a large amount of updates tonight. No sound from Flash or VLC, but Kaffeine works.

I am using the 64bit version of Flash from Adobe, it's been running fine for months.

---

### Post by vfontanela on 2009-10-14
I have the same problem, but I got no sound at all after the last updates:

vfontanela@vfontanela-laptop:/$ aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0


All channels are unmuted.

---

### Post by vfontanela on 2009-10-14
I have just upgraded, pulseaudio was upgraded but the problem persists.

:mad:

Help!

---

### Post by vfontanela on 2009-10-14
Ooops, working now. After update I went System, Preferences, Sound, Hardware and selected Analog Stereo Output.

---

### Post by SabreWolfy on 2009-10-14
No sound for me on Karmic Beta with latest updates and 82801G ICH7 Family card :( I *hate* regression bugs.

---

### Post by Nesaskewatch on 2009-10-14
Switching to analog works.  System -> Preferences -> Sound -> Hardware tab.  Under "Settings for the selected device", set the profile to "analog stereo duplex".

---

### Post by francsal on 2009-10-14
> **Nesaskewatch said:**
> Switching to analog works.  System -> Preferences -> Sound -> Hardware tab.  Under "Settings for the selected device", set the profile to "analog stereo duplex".

Ehhhmm.... sorry for being a PITA, but do you have any idea how to accomplish that in Kubuntu? In System Settings - Multimedia, there´s no way to make that switch. It just lists the "Device preference", and in every option (notifications, music, video, Comm, games and accesibility) it´s already setted to the Analog output (HDA Intel ALC888 )

Any help would be highly appreciated!

Cheers!

Frank

---

### Post by SabreWolfy on 2009-10-14
Deleted. Posted to incorrect thread.

---

### Post by clickwir on 2009-10-20
I was attempting to look at installing some other package, don't recall what one. And noticed that it wanted to install PULSEAUDIO. I thought that was the standard audio, but ... I don't know.

This install was an alpha6 cd install and has been upgraded since, so I don't know if it was left out and not needed at the time and now it is. But.... simply running this command and rebooting fixed my FLASH audio.

sudo apt-get install pluseaudio

Flash audio and VLC work fine now. :-)

---

### Post by arg0 on 2009-10-23
I had the same issue with Flash in Firefox. The reason was that the PCM volume was 0.
To get the audio back it was sufficient to run
$ alsamixer
and crank the PCM volume up.
Hope it will work also for you!

---

### Post by klemes on 2009-10-24
> **francsal said:**
> Ehhhmm.... sorry for being a PITA, but do you have any idea how to accomplish that in Kubuntu? In System Settings - Multimedia, there´s no way to make that switch. It just lists the "Device preference", and in every option (notifications, music, video, Comm, games and accesibility) it´s already setted to the Analog output (HDA Intel ALC888)

Any help would be highly appreciated!

Cheers!

Frank

I had the same issue with you on a HDA Intel soundcard with the same chipset as your (Realtek ALC 888).
For me the issue was fixed by adding this line in '/etc/modprobe.d/alsa-base' AND '/etc/modprobe.d/alsa-base.conf':

```
options snd-hda-intel model=auto
```

followed by:

```
asoundconf set-default-card Intel &&
sudo alsa force-reload
```

Give it a try I think it will fix your soundcard problems.
The above all are from the alsa-project.org website.

---

### Post by dresden on 2009-10-24
> **klemes said:**
> I had the same issue with you on a HDA Intel soundcard with the same chipset as your (Realtek ALC 888).
For me the issue was fixed by adding this line in '/etc/modprobe.d/alsa-base' AND '/etc/modprobe.d/alsa-base.conf':

```
options snd-hda-intel model=auto
```

followed by:

```
asoundconf set-default-card Intel &&
sudo alsa force-reload
```

Give it a try I think it will fix your soundcard problems.
The above all are from the alsa-project.org website.

thanks a lot klemes, here worked my sound is back.

---

### Post by klemes on 2009-10-24
Glad to have helped!!!!

:)

---

### Post by TGBaker on 2009-10-25
> **dresden said:**
> thanks a lot klemes, here worked my sound is back.

It didn't work on my system. I get a notification that hda intel alc888 could not be started and falling back to audiopulse.  But then I seem to have only a alsa-base.conf and not another file simply called alsa-base in modprobe.d????? I have sound but a low volume and noise at a higher volume with audiopulse. Any clues?

Thanks, 
Tommy

---

