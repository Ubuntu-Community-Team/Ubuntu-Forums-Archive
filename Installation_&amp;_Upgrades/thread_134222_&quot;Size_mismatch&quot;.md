---
title: "&quot;Size mismatch&quot;"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by DonQuixote on 2006-02-21
Anyone else experiencing this?

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
  Size mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb
  Size mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb
  Size mismatch

```

The fetching of these packages worked fine this morning.

Anywhere in particular I should be looking?

---

### Post by roncalg on 2006-02-21
just experienced "size mismatch". "synaptic" locked up. tried apt-get install -f ,twice.   "synaptic" still locked up.can anyone help?

---

### Post by drzaiusx11 on 2006-02-21
just got a "size mismatch" error trying to install abiword-gnome package using "apt-get install abiword" :(

---

### Post by mikcarol on 2006-02-21
got the same message trying to get tk8.4-dev; I tried to download it using the browser instead of apt-get and got the following in place of the download:

<br />
<b>Parse error</b>:  syntax error, unexpected T_STRING in <b>/u01/ftpubuntu/pub/ubuntu/pool/main/t/tk8.4/tk8.4-dev_8.4.6-1_i386.deb</b> on line <b>287</b><br />

script error maybe?

---

### Post by ewayte on 2006-02-21
According to William Grant on the ubuntu-users list:

"This is a known issue, and is plaguing repositories everywhere. There
are people working on it, and it should be fixed soon."

I tried installing gcc-3.4 from the US archive and got the same errors this evening.

---

### Post by sdb2028 on 2006-02-22
Just found this thread, having same probs too. At least now I know I'm not alone and can quit trying to figure out what I'm doing wrong. Going to try again in the morn. GL E1

---

### Post by mikcarol on 2006-02-22
:D The US archive is working

---

### Post by edgarde on 2006-06-15
4 months later and I'm having this problem.```
# apt-get -f --fix-missing install beep-media-player libsamplerate0 mpg123
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  beep-media-player libsamplerate0 mpg123
0 upgraded, 3 newly installed, 0 to remove and 99 not upgraded.
1 not fully installed or removed.
Need to get 1047kB of archives.
After unpacking 4108kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mpg123
Install these packages without verification [y/N]? y
Get:1 http://security.debian.org stable/updates/non-free mpg123 0.59r-20sarge1 [87.2kB]
Get:2 http://archive.ubuntu.com breezy/main libsamplerate0 0.1.1-2 [108kB]
Get:3 http://us.archive.ubuntu.com breezy/universe beep-media-player 0.9.7.1+cvs20050803-1ubuntu1 [852kB]
Fetched 1047kB in 7s (136kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.1-2_i386.deb  Size mismatch
Unable to correct missing packages.
E: Aborting install.
```I've tried it one package at a time and all at once, with and without each of the [FONT="mono"]**-f**[/FONT] and [FONT="mono"]**--fix-missing**[/FONT] options, and I've run [FONT="mono"]**apt-get clean**[/FONT].

I've tried removing "us." from this source:```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
```

I've tried this uncommenting source:```
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
```
And I've tried it without "us.".

How can this still be an issue? Very frustrated. I have a site where I occasionally support an Ubuntu box, so I don't know if this has been a problem continuously, or if this is a new instance of the same error.

---

