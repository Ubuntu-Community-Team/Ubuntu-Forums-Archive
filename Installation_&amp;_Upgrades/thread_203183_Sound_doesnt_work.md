---
title: "Sound doesnt work"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by PoisoN2003 on 2006-06-24
Well i upgraded my kernel and got my video to work but now in my new kernel the sound doesnt work and i dont even know where to start any help would be a appreciated

---

### Post by woedend on 2006-06-24
hello...can you give more details...such as what kind of sound card you have, when exactly the sound quit working(did it quit working after the kernel upgrade or never worked since install?)...any error messages?

---

### Post by PoisoN2003 on 2006-06-24
Okey ill try to tell u all i know

First in my old kernel where i am now sound and video works perfectly then i compiled the new 2.6.17-ck1 kernel
When i entered that nor the sound or video worked then i used a script to install my video card drivers so now the video works but sound still doesnt work.
I have creative sound blasters live or something like that
do u think it would work if i back up my old (from this where sound and video works) and replace the new one with this one?

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridg e
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a )
0000:00:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  0a)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600  Ultra] (rev a1)

``` 
hope this helps some how 
and i checked alsa mixer everything seems fine there

---

### Post by PoisoN2003 on 2006-06-24
NVM i fixed it :) HAPPY HAPPY

---

### Post by woedend on 2006-06-25
sorry I didnt get a chance to respond..glad you have it fixed.  would you mind posting how you fixed it so someone else may use it one day?

---

### Post by PoisoN2003 on 2006-06-25
I reinstalled the kernel 2.6.17 with the ck1 patch and then what i realized my problem was that the xorg on the last kernel was really small and only had the graphic stuff in it didnt have any sound so i gues that was my problem 
the xorg file was too small

---

