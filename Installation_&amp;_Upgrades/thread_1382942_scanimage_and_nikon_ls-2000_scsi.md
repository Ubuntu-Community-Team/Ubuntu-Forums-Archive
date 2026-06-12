---
title: "scanimage and nikon ls-2000 scsi"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by DrJohn999 on 2010-01-16
I installed my Nikon Coolscan LS-2000 on an adaptec 2940 scsi card. The card and scanner are recognized at boot, and the scanner is found by xsane at startup and by scanimage as follows:
```
~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `coolscan3:scsi:/dev/sg5' is a Nikon LS-2000 film scanner
device `coolscan:/dev/sg5' is a Nikon    LS-2000          slide scanner
device `hpaio:/usb/OfficeJet_V40?serial=MY219C414GWN' is a Hewlett-Packard OfficeJet_V40 all-in-one
```

Attempting anything else hangs scanimage and segfaults on ^C such as:
```
~$ scanimage -d coolscan:/dev/sg5 -T
^Cscanimage: received signal 2
scanimage: trying to stop scanner
Segmentation fault

```
Same result if I use the coolscan3:scsi:/dev/sg5 device

Loading libsane-extras fixed nothing. Powering off the OfficeJet fixed nothing.

In the theory that the scsi bus is failing at anything other than identifying attached devices (i.e. at higher speeds) I toggled the h/w termination but that made no difference.

I will try one more h/w resort: reduce the channel max speed from 40 MB/s to 10 and see if this helps.

But I suspect that it's more than that. Any ideas?

---

### Post by DrJohn999 on 2010-01-16
IO Speed to 10 MB/s has no effect. I tested SCSI transfers at-speed by chaining a drive on the back of the scanner -- runs flawlessly.

So, back to square 2 -- this probably is related to other sane / xsane / scanimage problems reported here and elsewhere with Karmic.

BTW -- I'm running x64 FWIW.

---

### Post by DrJohn999 on 2010-01-18
Fixed. While trying to get my flatbed Epson 3170 to go I added myself to the group 'saned'. Now to have some fun scanning those 30-year old Ektachromes... :}

---

### Post by mzmaffei on 2010-10-02
I am having a similar problem but not yet solved:
scanner is properly detected:
~$ scanimage -L
device `coolscan3:scsi:/dev/sg2' is a Nikon LS-2000 film scanner
device `coolscan:/dev/sg2' is a Nikon    LS-2000          slide scanner

but the use by xsane is impossible.
1- Selecting the "film scanner", xsane is stuck 
2- selecting the "slide scanner" xsane opens but with some error windows 
"Failed to obtain value of option source: invalid argument"

I tried to add my user to the group "saned" but no way to activate the scanner.

tried multiple options of 
~$ scanimage -v -T (with and without other parameters)
but the command is stuck

suggestions ?

---

### Post by DrJohn999 on 2010-10-02
Same problem here. Used to work in 9.10, but apparently after auto upgrading to 10.04 in May it seems to be broken again (first time I've tried it since the upgrade). The scanner shows up at /dev/sg6. Changing its group to 'scanner' had no effect (my username already is in the scanner and saned group), owner is root, permissions already were 660. The SCSI system seems to be working OK, scanner detection gives the same as before response to scanimage -L.

Currently stumped -- I'll try to get back to troubleshooting this in the near future. Maybe fixed in 10.10, we'll see.

---

### Post by DrJohn999 on 2010-10-02
OK, the problem seems to be the scanner hardware failing to initialize. As I was testing and rebooting, at one point I had the PC power off and I power cycled the scanner. It started up and ran through an initialization, making audible sounds as the device steppers ran. As I recall this did not happen previously.

Anyway, this time it scanned successfully, but only from the 'coolscan:/dev/sg6' item in the opening xsane dialog. Choosing the 'coolscan3:scsi:/dev/sg6' item failed with "...invalid argument." /dev/sg6 is used because I have four hard drives and two CDROM devices. You'll want to stick with whatever scanimage -L tells you.

At the command line level:

```
user@M4A78T:~$ scanimage -L
device `coolscan3:scsi:/dev/sg6' is a Nikon LS-2000 film scanner
device `coolscan:/dev/sg6' is a Nikon    LS-2000          slide scanner
device `hpaio:/usb/OfficeJet_V40?serial=MY219C414GWN' is a Hewlett-Packard OfficeJet_V40 all-in-one
user@M4A78T:~$ scanimage -T -d coolscan:/dev/sg6
scanimage: scanning image of size 1296x1947 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 3888 bytes...    PASS
scanimage: reading one byte...        PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...     PASS
scanimage: stepped read, 32 bytes...     PASS
scanimage: stepped read, 64 bytes...     PASS
scanimage: stepped read, 128 bytes...     PASS
scanimage: stepped read, 256 bytes...     PASS
scanimage: stepped read, 512 bytes...     PASS
scanimage: stepped read, 1024 bytes...     PASS
scanimage: stepped read, 2048 bytes...     PASS
scanimage: stepped read, 4096 bytes...     PASS
scanimage: stepped read, 4095 bytes...     PASS
scanimage: stepped read, 2047 bytes...     PASS
scanimage: stepped read, 1023 bytes...     PASS
scanimage: stepped read, 511 bytes...     PASS
scanimage: stepped read, 255 bytes...     PASS
scanimage: stepped read, 127 bytes...     PASS
scanimage: stepped read, 63 bytes...     PASS
scanimage: stepped read, 31 bytes...     PASS
scanimage: stepped read, 15 bytes...     PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS
user@M4A78T:~$ 

```
(important note: to see the scanner from scanimage, first quit from xsane)

I am using an Adaptec 2940 ultra-wide SCSI PCI adapter, by the way, with the scanner at ID:1 and the adapter at ID:7, termination turned on at the scanner, and set to auto for the adapter (at boot time). Actually the adapter is set to all defaults. The SCSI cable is only about 0.5-m long.

Hope this works for you.

Next challenge is to get the autofocus, exposure, gamma, etc to function well.

---

### Post by DrJohn999 on 2010-10-03
I fixed the autofocus and initialization problems by disassembling, cleaning, and lubricating the LS-2000. Not recommended if you don't have the tools and skills needed. If you do try this, whatever you do don't loosen any of the optical alignment screws; as it turned out it's quite possible to do a thorough cleaning and lubrication while leaving the optical bits intact. The rails were quite sticky, there was a little green corrosion around the metallic focus post, and the bottom mirror had collected its share of dust and fibers, which probably was the reason for the poor autofocus and strange-looking exposures.

When properly initialized the scanner light will blink slowly during the initialization and then turn on 100%. If initialization fails the light will blink rapidly before turning on 100%. The sound of steppers moving is a good indication that initialization is progressing.

Now I can see the grain again (at 2700 dpi) and of course every $*%@ spec of dirt on the negs.

One feature that xsane and xscanimage lack is control of the SA-20 filmstrip autofeeder. I also have the FH-20 manual filmstrip holder that goes into the MA-20 slide adapter. Simpler to use but not automated. Reportedly the FH-20 gives somewhat better focus than the SA-20 because it flattens most of the negative curl. Control of the SA-20 doesn't appear to be in the coolscan profile, and so far I haven't been able to get the coolscan3 profile to work. Running scanimage from the command line might give better control for some of the advanced features (haven't really tried it yet). Averaging doesn't seem to show up in xsane, but it is there in xscanimage. Should play around with icm profiles too.

I'll try to get coolscan3 working at some point.

---

### Post by mzmaffei on 2010-10-05
some more checks from my side:
checked carefully the power on and the startup sequence

SCSI ID is 2 as factory default

~$ scanimage -L
device `coolscan3:scsi:/dev/sg2' is a Nikon LS-2000 film scanner
device `coolscan:/dev/sg2' is a Nikon    LS-2000          slide scanner

scanimage works fine with 
~$ scanimage -T -d coolscan:/dev/sg2
[SIZE=1][COLOR=SeaGreen]scanimage: scanning image of size 1296x1947 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
....[/COLOR]
[/SIZE]
but NOT with 
~$ scanimage -T -d coolscan3:scsi:/dev/sg2
[SIZE=1][COLOR=Red]... failed invalid argument ....
[/COLOR][/SIZE]
but WORKS well with "**[COLOR=Lime]coolscan2[/COLOR]**" tag (why ?!? :confused::confused::confused:)
~$ scanimage -T -d coolscan2:scsi:/dev/sg2
[SIZE=1][COLOR=SeaGreen]scanimage: scanning image of size 1296x1947 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
...[/COLOR].
[/SIZE]
 
in xsane, no way to choose coolscan:/dev/sg2 or coolscan3:scsi:/dev/sg2:
I always get an "invalid parameter" at xsane startup 
BUT with different behaviours:

1- when I choose coolscan3:scsi:/dev/sg2, I have once the error and then xsane dies
2- when i choose coolscan:/dev/sg2, the error window is displayed three times and
    then xsane start working.... In this latter case I can get the image !

True you consideration about the "SA-20 STRIP FILM",: no way to use ?!?
acquiring some hundreds strip is impossible ...

---

