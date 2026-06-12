---
title: "Ububtu 7.10 sound issues"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by igggyc on 2007-10-14
**This post could be related to an Ubuntu bug filed at**: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello

I have just installed the pre-release of Ubuntu 7.10 Gutsy Gibbon with just 4 days until its release on my Dell Inspiron 1720. Everything appears to be fine, except I can't get my soundcard to work.

According to dell and my motherboard settings, the soundcard is a Sigmatel 9205.

I looked briefly on google and found this link:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

which seemed to address my problem. I followed the instructions there, my sound card still is not detected. the volume control symbol is crossed off by a little red circle and no sound plays.

At first I thought maybe the drivers provided on the link were wrong, so i went to the following site:

[http://www.gtlib.gatech.edu/pub/suse/projects/alsa/snapshot/driver/](http://www.gtlib.gatech.edu/pub/suse/projects/alsa/snapshot/driver/)

and downloaded the following file:

 alsa-driver-hg20071013.tar.bz2  and followed the first link's intructions on unzipping this file, yet still nothing works.

i must add i am not an experienced user, so any help for idiots such as myself would be greatly appreciated. i should also add that command: cat /proc/asound/card0/codec#* | grep Codec

comes back as invalid and fails to retrieve my codec info. it says "no such file or directory".

any help appreciated!!!!!

p/s/ all the unzipped files are in a directory caleld "alsa" located in home folder...

---

