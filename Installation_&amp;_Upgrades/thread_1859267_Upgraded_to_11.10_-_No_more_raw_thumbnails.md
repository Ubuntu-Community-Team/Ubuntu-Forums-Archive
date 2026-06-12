---
title: "Upgraded to 11.10 - No more raw thumbnails"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by Amon_Re on 2011-10-13
I just upgraded to Ubuntu 11.10 and I noticed that I no longer have thumbnails in Nautilus. Anyone know how to solve this (minor) issue?

---

### Post by OzzyFrank on 2011-10-15
Yeah, if you mean no picture preview thumbnails after the upgrade, same here. I actually have previews for vids, and the odd picture file scattered here and there, but in folders full of images, all I get is a generic JPG icon. And what's worse, when using Image Viewer and I hit F9 to show the Image Gallery at the bottom, instead of the previews I'm used to, all I get are the dark squares with red circle with a line through it like if a picture is corrupt, but these are all fine. Any ideas guys??

---

### Post by Meghnaad on 2011-10-17
I had a fresh Install of 11.10 
Most of the image file preview is available but no support for CR2 or NEF Images ! :confused:

---

### Post by scpatl4now on 2011-10-17
When I try to select images for use in other programs there is no preview either...which really is a problem when you have over 1000 images you are working with...hope there is a fix for this

---

### Post by Meghnaad on 2011-10-17
i can see Image previews with RawTherapee,
but unable to see preview in Nautilus !

---

### Post by searchfgold6789 on 2011-10-17
I'm a KDE user and having exactly the same problem in Dolphin, the default file manager for KDE.

---

### Post by adotei on 2011-10-17
From a previous post. Worked for me. Hope it works for you.

1. Open file manager. 
2. Edit->Preferences->Preview. Change preferences as required. 
3. Close file manager and open terminal.

4. Run the following command to install the necessary packages. 
> $ sudo apt-get install ffmpeg ffmpegthumbnailer gstreamer0.10-ffmpeg

5. Remove old thumbnails.
> $ rm ~/.thumbnails/fail/gnome-thumbnail-factory/*
$ rm ~/.thumbnails/normal/*

6. Open the file manager and enjoy your new thumbnails!

---

### Post by Meghnaad on 2011-10-18
Still no preview for NEF or CR2 Files,
gnome sushi gives a preview but not Nautilus

---

### Post by dFlyer on 2011-10-18
Here is the link to the bug report.

[https://launchpad.net/bugs/852923](https://launchpad.net/bugs/852923)

Maybe the more personal who file there will speed up a fix. I don't have thumbnails for sony arw or canon cr2.

---

### Post by scpatl4now on 2011-10-19
> **adotei said:**
> From a previous post. Worked for me. Hope it works for you.

1. Open file manager. 
2. Edit->Preferences->Preview. Change preferences as required. 
3. Close file manager and open terminal.

4. Run the following command to install the necessary packages. 


5. Remove old thumbnails.


6. Open the file manager and enjoy your new thumbnails!

Unfortunately, this did not work for me

---

### Post by obZen on 2011-10-19
Hello
I fixed it changing in /usr/share/thumbnailers/raw.thumbnailer the %i for %u

The result:```
[Thumbnailer Entry]
Exec=/usr/bin/gnome-raw-thumbnailer -s %s %u %o
MimeType=image/x-3fr;image/x-adobe-dng;image/x-arw;image/x-bay;image/x-canon-cr2;image/x-canon-crw;image/x-cap;image/x-cr2;image/x-crw;image/x-dcr;image/x-dcraw;image/x-dcs;image/x-dng;image/x-drf;image/x-eip;image/x-erf;image/x-fff;image/x-fuji-raf;image/x-iiq;image/x-k25;image/x-kdc;image/x-mef;image/x-minolta-mrw;image/x-mos;image/x-mrw;image/x-nef;image/x-nikon-nef;image/x-nrw;image/x-olympus-orf;image/x-orf;image/x-panasonic-raw;image/x-pef;image/x-pentax-pef;image/x-ptx;image/x-pxn;image/x-r3d;image/x-raf;image/x-raw;image/x-rw2;image/x-rwl;image/x-rwz;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;image/x-sr2;image/x-srf;image/x-x3f;
```

---

### Post by dFlyer on 2011-10-19
> **obZen said:**
> Hello
I fixed it changing in /usr/share/thumbnailers/raw.thumbnailer the %i for %u

The result:```
[Thumbnailer Entry]
Exec=/usr/bin/gnome-raw-thumbnailer -s %s %u %o
MimeType=image/x-3fr;image/x-adobe-dng;image/x-arw;image/x-bay;image/x-canon-cr2;image/x-canon-crw;image/x-cap;image/x-cr2;image/x-crw;image/x-dcr;image/x-dcraw;image/x-dcs;image/x-dng;image/x-drf;image/x-eip;image/x-erf;image/x-fff;image/x-fuji-raf;image/x-iiq;image/x-k25;image/x-kdc;image/x-mef;image/x-minolta-mrw;image/x-mos;image/x-mrw;image/x-nef;image/x-nikon-nef;image/x-nrw;image/x-olympus-orf;image/x-orf;image/x-panasonic-raw;image/x-pef;image/x-pentax-pef;image/x-ptx;image/x-pxn;image/x-r3d;image/x-raf;image/x-raw;image/x-rw2;image/x-rwl;image/x-rwz;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;image/x-sr2;image/x-srf;image/x-x3f;
```

Thanks, that fixed, I didn't the raw.thumbnailer file in /usr/share/thumbnailers so just created the file and now it all works. I will paste this fix under the bug report so other finding the bug report can fix it.

---

### Post by Meghnaad on 2011-10-21
Worked for me too !
Thanks !:popcorn:

---

### Post by awaldram on 2011-10-26
If you wish to use ufraw thumbnailer (active development supports modern cameras)

replace the exec= line with

```
exec=/usr/bin/ufraw-batch --embedded-image --out-type=png --size=%s %u --overwrite --silent --output=%o
```

Oh insure you have ufraw,ufraw-batch installed :)

---

### Post by sarang on 2012-02-27
I have been using the following custom script to create raw thumbnails. It overlays text indicating the raw file type (ORF / NEF / CR2 etc.) over the thumbnail image so as to make it easy to distinguish between a jpeg image and a raw image. Particularly useful when shooting in raw + jpg mode, where one gets two identical thumbnails (one for raw and one for jpg) and distinguishing between them requires careful inspection of the extension. This script eliminates the need for such careful inspection.
The following script is located at [FONT="Courier New"]/home/sarang/bin/my-raw-thumbnailer/my-raw-thumbnailer.bash[/FONT]
```

#!/bin/bash
# usage: my-raw-thumbnailer size inputfilename outputfilename

set -e

SIZE="$1";
INPUT="$2";
OUTPUT="$3";
RAW_STAMP="$(echo "$INPUT" | sed 's/.*\.//')";
RAW_STAMP="  ${RAW_STAMP^^}  ";

ufraw-batch --embedded-image --out-type=png --size="$SIZE" "$INPUT" --overwrite --silent --output=-| convert - -fill white -undercolor black -gravity SouthWest -pointsize 16 -font '/usr/share/fonts/truetype/ttf-droid/DroidSans-Bold.ttf' -annotate  +0+0 "${RAW_STAMP}" "$OUTPUT"

unset SIZE INPUT OUTPUT RAW_STAMP

exit 0


```

Also, [FONT="Courier New"]/usr/share/thumbnailers/raw.thumbnailer[/FONT] has:
```

[Thumbnailer Entry]
Exec=/home/sarang/bin/my-raw-thumbnailer/my-raw-thumbnailer.bash %s %u %o
MimeType=image/x-3fr;image/x-adobe-dng;image/x-arw;image/x-bay;image/x-canon-cr2;image/x-canon-crw;image/x-cap;image/x-cr2;image/x-crw;image/x-dcr;image/x-dcraw;image/x-dcs;image/x-dng;image/x-drf;image/x-eip;image/x-erf;image/x-fff;image/x-fuji-raf;image/x-iiq;image/x-k25;image/x-kdc;image/x-mef;image/x-minolta-mrw;image/x-mos;image/x-mrw;image/x-nef;image/x-nikon-nef;image/x-nrw;image/x-olympus-orf;image/x-orf;image/x-panasonic-raw;image/x-pef;image/x-pentax-pef;image/x-ptx;image/x-pxn;image/x-r3d;image/x-raf;image/x-raw;image/x-rw2;image/x-rwl;image/x-rwz;image/x-sigma-x3f;image/x-sony-arw;image/x-sony-sr2;image/x-sony-srf;image/x-sr2;image/x-srf;image/x-x3f;


```

Sample output is attached.

---

### Post by Lubelaczek on 2012-06-20
What about 12.04? I had no luck with this method. After creating raw.thumbnailer as described above still have no thumbnails for Canon's cr2. Anybody had success with this on "Precise"?

---

### Post by torlud on 2013-02-03
Using 12.04

Installed gnome-raw-thumbnailer, created raw.thumbnailer as in #11, then 

```
rm ~/.thumbnails/normal/* 			 		
```

then succeded displaying .cr2 thumbnails. Thanks!

---

