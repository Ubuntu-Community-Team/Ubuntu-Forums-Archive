---
title: "snd_hda_intel"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by kindian on 2005-11-30
Hi everyone.

I have a LG LW20 and for a while I have been experienced some problems with sound on my laptop.

```
$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 12)
0000:06:00.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:00.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:00.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:00.4 0805: Texas Instruments: Unknown device 8034
0000:06:02.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)

```

I found the solution for my problem by downloading the realtek audiopack from [http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True)

All you've got to do is extract the file and run 'sh install'.

It worked for me.

---

### Post by daller on 2005-12-01
Next time you post a howto, please use the title: "HOWTO: <title>"

---

### Post by JeffreyRatcliffe on 2005-12-04
[QUOTE=kindian]I found the solution for my problem by downloading the realtek audiopack from [http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True)

All you've got to do is extract the file and run 'sh install'.

It worked for me.[/QUOTE]

I have no sound from what lspci is reporting as a ALC882, so I tried this. I initially got

```
configure: error: no acceptable C compiler found in $PATH
```

and saw that gcc wasn't installed by default.

I then got

```
configure: error: C compiler cannot create executables
```

which I fixed with

```
sudo apt-get install build-essential
```

The automatic install is now falling over with the following error:

```
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
Remove Folder.....
./install: line 89: alsaconf: command not found
```

ncurses is installed. The manual install instructions seem to be based on an old version of the driver and so don't work either.

Has anybody tried this since they updated the driver on the 02.12.2005?

Thanks

Jeff Ratcliffe

---

### Post by kindian on 2005-12-11
Ok, there's no sound on headphones. Any idea?

---

### Post by anarchist_hippy on 2005-12-26
[QUOTE=kindian]

All you've got to do is extract the file and run 'sh install'.

It worked for me.[/QUOTE]

You should run 

```
 **sudo** sh install 
```

For root access.... 
;)

---

### Post by goterror on 2008-07-23
> **JeffreyRatcliffe said:**
> 

./install: line 89: alsaconf: command not found[/CODE]



Just download the alsa-utils package from DEBIAN.ORG NOT UBUNTU! Then [LIST=1]
dpkg-deb -x "your deb file" dir
[/LIST]
[LIST=2]
cp the alsaconf file within the dir directory to some place like /usr/sbin
[/LIST]

I assume you can solve the little problem with the permission and the /dev/dsp detail in later.

Have fun

---

