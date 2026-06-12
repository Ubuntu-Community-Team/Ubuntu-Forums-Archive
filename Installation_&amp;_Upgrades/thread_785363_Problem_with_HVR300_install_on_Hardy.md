---
title: "Problem with HVR300 install on Hardy"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by glenpcarter on 2008-05-07
I'm hoping someone can help, I am a newbie to Linux and have spent a week so far trying to sort this problem with no solution.

I have installed a fresh install of Ubuntu Hardy and everything installs ok and when I check the HVR3000 has installed ok and i can see adapter0 in /dev/dvb/ I want to get the multi frontend working on this by following [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000) . I can patch and make and make install with no errors but when i check my /dev/dvb/adapter0 has now disappeared and if I check dmesg it come up with lots of unknown strings. Could someone please point me in the direction of a solution.

Thanks
Glen

---

### Post by evolutionx on 2008-05-29
> **glenpcarter said:**
> I'm hoping someone can help, I am a newbie to Linux and have spent a week so far trying to sort this problem with no solution.

I have installed a fresh install of Ubuntu Hardy and everything installs ok and when I check the HVR3000 has installed ok and i can see adapter0 in /dev/dvb/ I want to get the multi frontend working on this by following [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000) . I can patch and make and make install with no errors but when i check my /dev/dvb/adapter0 has now disappeared and if I check dmesg it come up with lots of unknown strings. Could someone please point me in the direction of a solution.

Thanks
Glen

Hey,

I have the exact same card and problem after running through the guide.  I just found something interesting however. Seems its now under /dev/video0 ??  Hope someone can help :)

 Linux version 2.6.24-17-generic

 xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-17-generic)
looking for available devices
port 355-386
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 387-418
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Hauppauge WinTV-HVR3000 TriMode
    flags:  capture tuner 

This is what dmesg shows me.

[   49.451180] cx88[0]: subsystem: 0070:1402, board: Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T [card=53,autodetected]
[   49.451187] cx88[0]: TV tuner type 63, Radio tuner type -1
[   49.606546] tveeprom 0-0050: Hauppauge model 14109, rev B3D3, serial# 2687690
[   49.606553] tveeprom 0-0050: MAC address is 00-0D-FE-29-02-CA
[   49.606558] tveeprom 0-0050: tuner model is Philips FMD1216MEX (idx 133, type 4)
[   49.606565] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   49.606571] tveeprom 0-0050: audio processor is CX882 (idx 33)
[   49.606575] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   49.606580] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   49.606584] cx88[0]: hauppauge eeprom: model=14109
[   49.606804] input: cx88 IR (Hauppauge WinTV-HVR300 as /devices/pci0000:00/0000:00:1e.0/0000:02:0d.0/input/input4
[   49.639854] nvidia: module license 'NVIDIA' taints kernel.
[   49.648291] cx88[0]/0: found at 0000:02:0d.0, rev: 5, irq: 20, latency: 64, mmio: 0xeb000000
[   49.648395] cx88[0]/0: registered device video0 [v4l2]
[   49.648460] cx88[0]/0: registered device vbi0
[   49.648528] cx88[0]/0: registered device radio0
[   50.020939] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   50.021019] cx88[0]/2: cx2388x 8802 Driver Manager
[   50.021045] ACPI: PCI Interrupt 0000:02:0d.2[A] -> GSI 21 (level, low) -> IRQ 20
[   50.021059] cx88[0]/2: found at 0000:02:0d.2, rev: 5, irq: 20, latency: 64, mmio: 0xed000000
[   50.108084] cx2388x alsa driver version 0.0.6 loaded
[   50.108181] ACPI: PCI Interrupt 0000:02:0d.1[A] -> GSI 21 (level, low) -> IRQ 20
[   50.108224] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   50.134898] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[   50.134934] usbcore: registered new interface driver usblp
[   50.205653] cx88_dvb: Unknown parameter `frontend'
[   50.229756] usbcore: registered new interface driver hiddev

Thanks in advance :)

---

### Post by evolutionx on 2008-06-01
Well I ran through the setup once more on the guide [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000) and choose the Satellite only single front end kernel patch and I am able to watch satellite TV.

Still not able to get the multiple front end working.

---

