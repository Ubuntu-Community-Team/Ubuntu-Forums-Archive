---
title: "Hardy, VLC &amp; Libdvdcss2 (IFO file problems)"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by joebrueske on 2008-06-04
Okay, so I was finally able to get Libdvdcss2 installed in Hardy
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


I'm trying to play my MST3K: Boggy Creek 2 disc and the error was a css error. So I just installed CSS2 library and thought it would work. Nope. VLM Crashes so I ran it in terminal and got this:
> libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: MST3K_BOGGY_CREEK_II
libdvdnav: DVD Serial Number: 3FD62815___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/joe/.dvdnav/MST3K_BOGGY_CREEK_II.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000128
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000176
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001852d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0001a340
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0001a379
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0001ef7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0001efb3
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted


I am searching online to see if anyone else has had similar problems, but I haven't found anyone yet. Let me know if anyone has any ideas.

EDIT:
I found a patch to patch the IFO system in libdvdread3 [http://www.nabble.com/-Bug-38118--libdvdread3,-ASSIGNED:-There-are-some-DVDs-which-can-not-be-played-by-a-DVD-player-using-libdvdread-,-like-e.g.-VLC.-This-is-due-to-the-defective-UDF-file-system-produced-by-the-copy-protection-DVD-Movie-Protect-td15705939.html]("http://www.nabble.com/-Bug-38118--libdvdread3,-ASSIGNED:-There-are-some-DVDs-which-can-not-be-played-by-a-DVD-player-using-libdvdread-,-like-e.g.-VLC.-This-is-due-to-the-defective-UDF-file-system-produced-by-the-copy-protection-DVD-Movie-Protect-td15705939.html"). However I don't know what I'm suppose to patch it against. I'm assume I would just have to copy and paste it or use dpatch right? Thanks again

---

### Post by mc4man on 2008-06-04
_If_ the patch will help here is easiest way to apply (for vlc, totem)
[http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)
 basically you open a terminal and add gpg key
```
wget -qO - http://tobias.rautenkranz.ch/tobias.rautenkranz.asc | sudo apt-key add -

```
open admin -> software sources -> third party and add the repo
```
deb http://tobias.rautenkranz.ch/debian stable/

```
run ```
sudo apt-get update
``` then
```
sudo apt-get install libdvdnav-ifo4
```
Before trying vlc again go to home dir. (show hidden files) find .dvdcss and delete any folders inside  (eliminates possiblity of corrupted key files)
The patch doesn't work against some recent adv. structure protections

note : for mplayer you need to apply the dvdread patch to source and then build

---

### Post by joebrueske on 2008-06-05
Mc4Man I appreciate the code and the tip on that key storage. I didn't even bother looking in there when I updated the css keys to version 2. It's possible that was even the problem, but I'll never know unless I do it all over again. But I don't want to. lol

I now have the video playing without sound... hmmm... another oddity. Though, I think I already saw this one though. Time to troubleshoot with other DVDs! Woo hoo!

EDIT
It turns out that without the ALSA backports installed you can't have VLC and another app using the same sound drivers. It's odd that VLC has the audio muted but it's still playing. Oh well, it works!

---

### Post by mc4man on 2008-06-05
sometimes a sound issue in vlc can be fixed by setting -> preferencs -> enable advanced options -> audio -> output modules -> change from default in the drop down to something specific (alsa is a good choice)


edit : system wide is in system -> preferences -> sound, move settings off of auto detect to a specific choice

---

