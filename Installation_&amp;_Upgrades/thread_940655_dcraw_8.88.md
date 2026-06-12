---
title: "dcraw 8.88"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by manuel.camacho on 2008-10-07
Can any one tell me when the 8.88 release of DCRAW is likely to be approved ?.
tks

---

### Post by Cannaregio on 2008-10-07
I'm also very interested.
For instance, the small but gorgeous panasonic lumix lx3, (for street photography, with that "dynamic" b&w mode, almost as good as, and for sure more silent than, a leica rangefinder), uses ".RW2" raw files that are  recognized atm only by the awful silkypix, windows only proprietary application, AND by the last version "8.88" of dcraw.

Photoshop & company don't yet recognize RW2 files.
So the gimp (and all other applications using dcraw) could, for once, quickly be at the avantgarde :-)

I tried installing dcraw 8.88-5.1.i586.rpm with alien-d and then dpkg -i, and I can dcraw -T for tiff files, but for  reasons that escape me, rawtherapee gives a "[COLOR="DarkRed"]Corrupted memory profile[/COLOR]" errormsg and does not open correctly my rw2 files.

Anyone has or has had better experiences?

Here the errors by rawtherapee:
```

rawtherapee P1000386.RW2 
/usr/share/rawtherapee/gtkrc:50: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/rawtherapee/gtkrc:51: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/rawtherapee/gtkrc:52: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/rawtherapee/gtkrc:53: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:41: Invalid symbolic color 'fg_color'
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:41: error: invalid identifier `fg_color', expected valid identifier
processing file /usr/share/rawtherapee/profiles/crisp.pp2...
processing file /usr/share/rawtherapee/profiles/default.pp2...
processing file /usr/share/rawtherapee/profiles/neutral.pp2...
Opening file P1000386.RW2 (P1000386.RW2, .)
Loading Panasonic DMC-LX3 image from P1000386.RW2...
P1000386.RW2: Unexpected end of file
Scaling with darkness 0, saturation 65520, and
multipliers 1.000000 0.549061 0.903967 0.549061
unknown tag: 0x24
unknown tag: 0x25
unknown tag: 0x26
unknown tag: 0x27
unknown tag: 0x2d
unknown tag: 0x118
unknown tag: 0x119
===== IFD =====
<0x110> Model = DMC-LX3                                  (count=8)
<0x11a> XResolution = 1                                        (count=1)
===== Exif =====
===== GPS =====
<0x3> GPSLongitudeRef = 2538                                     (count=1)
<0x4> GPSLongitude = 6                                        (count=1)
<0x5> GPSAltitudeRef = 8                                        (count=1)
<0x6> GPSAltitude = 2526                                     (count=1)
<0x7> GPSTimeStamp = 3784                                     (count=1)
<0x8> GPSSatelites = 1                                        (count=1)
<0x9> GPSStatus = 4                                        (count=1)
<0xa> GPSMeasureMode = 12                                       (count=1)
<0xb> GPSDOP = 34316                                    (count=1)
<0xd> GPSSpeed = 1                                        (count=1)
<0xe> GPSTrackRef = 4095                                     (count=1)
<0xf> GPSTrack = 4095                                     (count=1)
<0x10> GPSImgDirectionRef = 4095                                     (count=1)
<0x17> GPSDestBearingRef = 250                                      (count=1)
<0x18> GPSDestBearing = 0                                        (count=1)
<0x19> GPSDestDistanceRef = 0                                        (count=1)
<0x1a> GPSDestDistance = 0                                        (count=1)
<0x1b> GPSProcessingMethod = (Undefined)                              (count=26)
<0x1c> GPSAreaInformation = 0                                        (count=1)
<0x1d> GPSDateStamp = 0                                        (count=1)
<0x1e> GPSDifferential = 0                                        (count=1)
===== IOP =====
<0x1> InteroperabilityIndex = (Undefined)                              (count=4)
<0x2> InteroperabilityVersion = 3836                                     (count=1)
===== MakerNote =====
setscale before lock
setscale starts (479, 317)
freeall starts 0
setscale ends
setscale ends2
Applying white balance, color correction & sRBG conversion...
rot=0, hf=0, vf=0
setscale before lock
setscale starts (479, 317)
setscale ends
setscale ends2
ICM TIME: 5957
lcms: Error #12288; Corrupted memory profile
INIT: 664748
TRANSFORM: 95
BLURMAP: 39
RGB: 57423
LUMINANCE: 13192
COLOR: 4509
RGBCONVERT: 34436
Total processing time: 790207

```

Also note that [COLOR="DarkRed"]P1000386.RW2: Unexpected end of file[/COLOR] errormsg.

---

### Post by Cannaregio on 2008-10-07
Found what's the problem.
Mybad I believed that rawtherapee and ufraw would automagically use the last version of dcraw installed on the box.

Great thanks for the following (and for his gorgeous work on dcraw) to Dave Coffin, the author of dcraw.

```
rawtherapee and ufraw are using code from an older
version of dcraw.c, so they do not yet support the LX3.
You need to ask their developers for an update
``` 

This I will do asap.

---

### Post by Cannaregio on 2008-10-08
Ok, according to their respective authors (Bytec & Udi Fuchs), Both the next RawTherapee v2.4 and the next UFRaw-0.14 will 
have the latest dcraw version, and then support the lx3's raw files.
Rawstudio 1.1 (published on 15 september) does not use the latest dcraw version (8.88, that incidentally appeared on 2008/09/15 22:29:19).

So we gotta wait just a little :-)

---

### Post by Cannaregio on 2008-10-09
Since I have hijacked this thread, and while still awaiting dcraw implementation in ufraw, rawtherapee, rawstudio and the gimp, I will take this thread opportunity to have a look at the "best" dcraw command line commands for my RW2 raw files from the lumix lc3

At the moment I am using
```
dcraw -4 -T -w *.RW2
```

-4 linear rgb
-T tiff
-w cmeras white balance

I tried different colorspaces ("-o 2" for instance) and didn't see any relevant difference.

Anyone has better ideas?

---

### Post by Cannaregio on 2008-10-11
See also this interesting discussion:
[http://forums.dpreview.com/forums/read.asp?forum=1033&message=29638301]("http://forums.dpreview.com/forums/read.asp?forum=1033&message=29638301")

Where a batch file is proposed:
```
dcraw -v -w -H 2 -o 0 -q 3 -T -S 4095 -b 2 -P badpixels.txt %1
```

and a lot more (re: barreling) is discussed.

Btw, [COLOR="Blue"]-H 2[/COLOR] and not [COLOR="#0000ff"]-H 1[/COLOR] for the following reason:
"never [COLOR="Blue"]NEVER use -H 1[/COLOR] for developing photographic stuff. 

If you are lucky and your RAW file has 0 pixels saturated, -H 1 will do exactly the same as -H 2. But if your RAW file has some blown area (sun, lightbulbs, overexposed sky,...) which is very common, -H 1 will produce channel misalignment in those areas meaning a disgusting magenta/pink colour on them.

[COLOR="#0000ff"]Use -H 2 instead[/COLOR] which will produce an image with the same exposure as -H 1 but always ensuring blown highlights are 100% neutral (R=G=B)" (Guillermo Luijk)


ALso interesting are the extra infos by Guillermo Luijk @:
[http://forums.dpreview.com/forums/read.asp?forum=1018&message=29677170]("http://forums.dpreview.com/forums/read.asp?forum=1018&message=29677170")
where you can read the following:

"If you want an Adobe RGB output, use straight -o 2. This will produce an Adobe RGB image with correct colours. In addition to this, the linear (gamma=1.0) profile info will be embedded into the output TIFF file so Photoshop will automatically recognize it when opening the TIFF file. On other software you will just need to assign the TIFF to a linear version of Adobe RGB"

-o 0 yields an image in the camera RGB space (unlike -o 2, it does not perform any profile conversion), so unless you have done camera profiling to assign your particular camera's response, -o 0 will produce wrong (dull and desaturated) colours no matter to which profile you assign it in Photoshop.

If you like to play with the DCRAW command line, there is a group of French crazy coders adding really advanced features into it like gamma, micro contrast, exposure control,...
Just check: [http://www.chassimages.com/forum/index.php?topic=17010.160]("http://www.chassimages.com/forum/index.php?topic=17010.160") 


An example of DCRAW command line they are using (they finished using the A-Z alphabet so started to use symbols for the new functions):

```
dcrawggt87 -v -w +M -H 2 -o 4 -I 1 -q 3 -l 2 8 -C 0.9995 0.9998 -g 7 -N 2 1 3 -@ 1.1 1.1 1.0 -Z 1.2 3 -[ 1.0 30 4 -% 1.4 60 -Y 2 1.0 -4 -T DSC_0416.NEF
```

---

### Post by manuel.camacho on 2008-10-11
Thanks for keeping things spinning.
I have with help compiled dcraw 8.88 and it works with RW2 files from my panasonic fx28. As dcraw is used elsewhere, for safety's sake, I have kept v8.88 seperate.
Working fom the command line is no real chore and I can wait for the official upgrade.

---

### Post by boarderpatrol on 2008-10-14
My wife has a new Panasonic fz-28 as well.  Loves the camera btw.  Look forward to the new release to support the rw2 files.  Not sure I can compile the 8.88 version of dcraw myself.  I think I currently have 8. something.   

   Thx for the great info.   subscribed to thread.

---

### Post by Cannaregio on 2008-10-30
It's done!
Not only dcraw 8.88 but now also two different GUI implementations of it:

[COLOR="#0000ff"]RAWTHERAPEE[/COLOR] 24 beta 1
and
[COLOR="#0000ff"]UFRAW[/COLOR] 0.14

can now work with the raw files "[COLOR="Blue"]RW2[/COLOR]" of the gorgeous panasonic LX3 (and incidentally with other recent raws like those produced by the new sony a900).
Rawstudio and LightZone should follow before the end of the year.
Careful with F-spot, it might not want to load your rw2 files automatically and just take the jpegs. So for the moment you might want to load the RW2 files per hand into f-spot's relevant folder locations.

This said [Dcraw]("http://en.wikipedia.org/wiki/Dcraw") remains so powerful, fast and effective it is well worth learning and using in its own command line ways (see postings above) without any distracting GUI whatsoever :-)

All Heils to Dave Coffin (dcraw Author)!

And with this this thread is finished :-)

---

