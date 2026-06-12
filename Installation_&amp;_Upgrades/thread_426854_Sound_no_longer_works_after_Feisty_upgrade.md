---
title: "Sound no longer works after Feisty upgrade"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Explodinglemur on 2007-04-28
My sound was working fine on my Asus A8Jm laptop (Intel HDA audio) with Dapper, and continued working when I upgraded to Edgy.  However, upon upgrading to Feisty, my sound does not work anymore.  Everything appears to be working fine, there's just nothing coming out of the speakers.

lspci -vv output:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1153
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
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

Contents of /proc/asound/cards:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 23
```

aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I tried the aptitude purge linux-sound-base alsa-base alsa-utils trick, reinstalled said packages, and rebooted.  Still no sound.
Also added options snd-hda-intel index=0 to /etc/modprobe.d/alsa-base, tried model=laptop.
I do not have any .asoundrc or asound.conf files on the system.  I do not see any errors in dmesg or in /var/log/messages.  If I play someting in Rhythmbox, it thinks it's playing, but I just don't hear anything.  Volume controls work, nothing is muted.  I'm not sure what to try next, and I don't know why things would have suddenly stopped working in Feisty when Edgy and Dapper worked great.

---

### Post by zerosystem on 2007-04-28
I think my problem might have been the same as yours.

I didn't upgrade to feisty, I did a clean install, but I noticed that in:

(volume icon on the upper taskbar) 
'open volume control' > 'swtiches' (tab)

For some reason, the digital output box was checked (I had my speakers plugged into the normal line out plug) so I wasn't getting any sound.

---

### Post by Explodinglemur on 2007-04-28
I don't have a digital output on my laptop, and I've already tried toggling the switches in the mixer app.  No effect.

---

### Post by Explodinglemur on 2007-04-29
Aha!  I just found this:
[https://bugs.launchpad.net/ubuntu/+bug/103699](https://bugs.launchpad.net/ubuntu/+bug/103699)

Installed the modules listed in that thread, now I have sound again.

---

