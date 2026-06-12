---
title: "Problem upgrading 8.04LTS to 10.04LTS"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by davesmith on 2011-05-02
hi

I use 8.04LTS because I cannot upgrade to 10.04. I have a fairly old  Toshiba Satellite A30 and everything works with hardy - my cd/dvd  rewriter, audio and video (with acceleration) display etc.

I have tried for a month now to upgrade to 10.04 without success. It  will not load on a live cd but black screens halfway through - i think  its a graphics issue, i get a set of coloured squares like big pixels  after the purple screen and it dies. It does the same on the re-boot  after upgrade via update manager

So I have a problem, what to do after 8.04LTS finishes shortly? Does anyone have  any ideas on what I can do to solve this and achieve a successfull  upgrade?

Thanks

---

### Post by mörgæs on 2011-05-02
Please give the hardware specifications.

---

### Post by davesmith on 2011-05-03
Thank you for a quick reply
 
Could you post the terminal code that will call up the hardware info that you require? I will post the output

Regards

---

### Post by mörgæs on 2011-05-03
```
hwinfo --cpu
hwinfo --memory
```

---

### Post by davesmith on 2011-05-03
output of hwinfo --cpu is

01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j9NaKXXZtZ69
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 15.2.9 "Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,up,pebs,bts,cid,xtpr
  Clock: 3066 MHz
  BogoMips: 6128.44
  Cache: 512 kb
  Units/Processor: 1
  Config Status: cfg=new, avail=yes, need=no, active=unknown

____________________________________________________________

output of hwinfo -- memory

01: None 00.0: 10102 Main Memory                                
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0x7ca43fff (rw)
  Memory Size: 2 GB 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

__________________________________________________________________

Is this what you needed?

Regards

---

### Post by mörgæs on 2011-05-03
It is a fine machine for Ubuntu. Go for a clean install, not an upgrade. 

If you can not boot a normal CD, you might find some advice here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

I guess that especially the part about boot options is of value to you. Toshibas often need this.

By the way, please post also the result of 
```
hwinfo --gfxcard
```

---

### Post by davesmith on 2011-05-03
output of hwinfo -- gfx

22: PCI 02.1: 0380 Display controller                           
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3582_0
  Unique ID: ruGf.tPfDh0fMD49
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Toshiba America Info 855 GM"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3582 "855 GM"
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xff00 
  Revision: 0x02
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Memory Range: 0xe0080000-0xe00fffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d00003582sv00001179sd0000FF00bc03sc80i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3582
  Unique ID: _Znp.tNELGlTPTr3
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Toshiba America Info 855 GM"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3582 "855 GM"
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xff00 
  Revision: 0x02
  Memory Range: 0xe8000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xe0000000-0xe007ffff (rw,non-prefetchable)
  I/O Ports: 0x1800-0x1807 (rw)
  IRQ: 16 (476252 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00003582sv00001179sd0000FF00bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #23
_______________________________________________________________________________

Yes, it is a nice m/c for ubuntu and I want to solve this upgrade!

I have successfully installed 10.10 maverick - but there was an audio problem (severe distortion) and jerky video playback using VLC, Also 10.10 would not burn CD's - but would play them. It was a clean install - but I had to keep tapping the shift key or it hung. 10.04 installed cleanly from the disk - but crashes when it tries to start the x-server. Every time. :(

I think the 10.04 install problem is solvable, but I would like some help! 

I have read the link [http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857) and tried many of the suggestions....

Regards

---

### Post by mörgæs on 2011-05-03
If you want to get 10.04 running, here are some suggestions:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Have you tried 11.04?

---

### Post by mörgæs on 2011-05-03
For burning CD's, have you tried Gnomebaker?

---

### Post by davesmith on 2011-05-03
I tried booting with the F6 key nomodset option, it didnt work :sad:

Yes 11.04 loaded with a clean install. Whatever is this blackscreen problem, it is solved for both 10.10 and 11.04. - but I got audio/video playback problems and the cd burner issue.

Thank you for the link [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) Is it necessary to apply the patches in hardy, before the 10.04 install, or during it?

Regards

---

### Post by davesmith on 2011-05-03
I didnt try Gnomebaker but will next time, tnx

Regards

---

### Post by kansasnoob on 2011-05-03
> **davesmith said:**
> I tried booting with the F6 key nomodset option, it didnt work :sad:

Yes 11.04 loaded with a clean install. Whatever is this blackscreen problem, it is solved for both 10.10 and 11.04. - but I got audio/video playback problems and the cd burner issue.

Thank you for the link [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) Is it necessary to apply the patches in hardy, before the 10.04 install, or during it?

Regards

The nomodeset option is wrong for your i855 gpu, you want to use "i915.modeset=1".

> From the LiveCD:

1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu.

2) Hit Enter to select your language, and then press F6 and then Esc.

3) Add "i915.modeset=1" after "quiet splash".

4) Press Enter to boot the LiveCD. 

> From an installation:

1) Hold down Shift while booting to enter the GRUB menu.

2) Press 'e' to edit.

3) Add "i915.modeset=1" after "quiet splash".

4) Ctrl+x to boot.

If adding "i915.modeset=1" to your boot parameters allows you to boot successfully, you then need to enter the following commands into a terminal to make the changes permanent. 

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
```

```
sudo update-initramfs -u
```

Let us know how that goes :)

---

### Post by davesmith on 2011-05-03
kansasnoob, that worked:D  i am running on the live 10.04.02LTS cd!!

now i'll try the proper install :D:D

may i ask why the intel drivers were disabled in the first place? the i855 chip gives good video acceleration 

Many kind regards

---

### Post by davesmith on 2011-05-04
I have successfully installed 10.04LTS making permanent the i915.modeset=1 change and it boots nicely every time. 

The graphic display and firefox seem ok, no freezes after I applied Stephan's updated intel driver, no jerky cursor

But audio is distorted and mplayer will not play .avi movies in sync with audio 

So i wonder if video acceleration is working in the 855 gfxcard, is there terminal code that will tell me?

Regards

---

### Post by mörgæs on 2011-05-04
Probably best to search this forum:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by davesmith on 2011-05-05
You guys did help - I did manage to install 10.04LTS and got it running but it definatly is not stable on my Tosh. It will freeze up if i try and play music or a film - no matter what player I use. Or what patch I apply

Disabling the 855 gfx chip might have allowed very fast booting - but this issue has been giving me a headache for a year or more now. 10.10 and 11.04 both load but dont seem to support my hardware.

After reading some of the other forums, it seems lots of ppl using Toshiba machines have issues like this!

I dunno what to do now...

Regards

---

### Post by mörgæs on 2011-05-05
Then you could try another (unrelated) distro for comparison. 

Slitaz, for example. Not because it is small, but because it is not a Debian.

---

### Post by davesmith on 2011-05-05
I have not given up on Ubuntu. Hardy Heron was very stable, ran everything I needed (even my Epson printer/scanner) I liked it!

There is still a few days left before hardy is no longer supported. My friend Ratspeaker has offered to visit and have a look. This weekend will give us some time to try once more. We plan to have another look at 11.04 - it installed nicely,didnt freeze but maybe I needed some codex for the media?

Regards

---

