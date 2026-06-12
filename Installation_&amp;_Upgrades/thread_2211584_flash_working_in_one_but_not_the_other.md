---
title: "flash working in one but not the other"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by jdefed on 2014-03-16
Hi;
I have 2 desktops running lubuntu 12.04lts. One I have been using for several years and flashplayer is working, using chromium as browser. The other I just installed and cannot get flash to work. Are there some folders that I can copy from working pc and paste in nonworking pc to get flash working. Both are up to date as far as update manager. I did try originally to clone the working drive to the other pc, but the working pc is all amd video and cpu, and the other has an invidia video card. I couldnt get the invidia to work with the amd drivers I guess, so thats why I did a clean install.
Thanks
jim

---

### Post by slooksterpsv on 2014-03-16
The other is running chromium as well? Check about:plugins in the address bar and see if it shows Flash. If not download flashplugin-installer

---

### Post by jdefed on 2014-03-16
Both running the same default programs. Yes chromium shows the same plugins in both. I'm using the same monitor for both pc's, so I can't easily compare installed programs. I was hoping that all the plugins are in some folder like usr/lib so I could copy and paste, but if I have to go line by line in packet manager I guess I will. Just looking for some easy way.

---

### Post by slooksterpsv on 2014-03-16
The easiest way is to install the flashplugin-installer

It's in the software center. Just search for that term and it'll show up in the software center. If that doesn't work you can copy it from your other system I believe its located... let me find it: /usr/lib/flashplugin-installer/libflashplayer.so - I'm not sure how Chrome/Chromium knows to look there or if it does if manually installed.

---

### Post by jdefed on 2014-03-18
I found this thread that said my cpu does not support flashplayer 11.2 (latest version). Apparantly the cpu needs sse2 and I only have sse. So I'm trying to install ver 10, but I am not having much luck. Can I download older versions in packet manager or does it have to be done in terminal. I tried a copy and paste method I found but couldn't make it work. I'm not that good in terminal so I would need some detailed instructions or give me a link to help me.
thanks
jd

---

### Post by slooksterpsv on 2014-03-18
[https://wiki.mageia.org/en/Flash_Plugin_Installation](https://wiki.mageia.org/en/Flash_Plugin_Installation) - you can try that

Or yoou can try.. hmm this - [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)

If you follow this guide: [http://www.upubuntu.com/2012/06/how-to-install-flash-player-11-manually.html](http://www.upubuntu.com/2012/06/how-to-install-flash-player-11-manually.html) - on how to install it. The archive is taking forever to download, but you only need the libflashplayer.so file and install that in /usr/lib/firefox - for chrome I'm not sure where to put it. And try that. Other than that I never thought of unsupported CPU features being a reason flash didn't work. Odd.

---

### Post by slooksterpsv on 2014-03-18
Dang right as I clicked submit it changed from 10 min to being open. Ok so you have to extract from: 11_1r102_63_32bit the flashplayer11_1r102_63_linux.i386.tar.gz file, extract that and put all those files/folders in the proper places (see the guide upubuntu.com/ that I posted above for how to do that)

---

### Post by sam40 on 2014-03-18
&#25265;&#27465;&#25265;&#27465;&#65292;&#30475;&#19981;&#25026;&#21834;&#30475;&#19981;&#25026;&#21834;

---

### Post by slooksterpsv on 2014-03-19
&#19979;&#36733; - [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)
&#20174;&#23384;&#26723;&#20013;&#25552;&#21462;&#25991;&#20214;&#36827;&#20837;linux&#30340;32&#20301;&#25991;&#20214;&#22841;&#24182;&#35299;&#21387;&#25991;&#20214;11_1r102_63_32bit&#30340;flashplayer11_1r102_63_linux.i386.tar.gz 
&#36816;&#34892;&#19979;&#38754;&#30340;&#21629;&#20196;&#25226;&#23427;&#25918;&#22312;&#36866;&#24403;&#30340;&#20301;&#32622;&#65306; 
sudo cp -r libflashplayer.so /usr/lib/firefox/plugins 

sudo cp -r usr/* /usr

Extract the files from the archive, go into the 32-bit folder and extract the files from the:
11_1r102_63_32bit the flashplayer11_1r102_63_linux.i386.tar.gz
You should be able to run the following commands above to move the files to the needed directory.

---

### Post by jdefed on 2014-03-19
I followed the first instructions and now have video, but no audio. could this be from the flashplugin? I can play audio cd's, so sound is working. Alsamixer has everything unmuted and turned up.

---

### Post by slooksterpsv on 2014-03-19
I wanna bet that this issue is happening in Chrome - reason I ask is cause this was an issue with Chrome/Chromium.
I'd try firefox or the suggestions on this page - [https://bbs.archlinux.org/viewtopic.php?id=134892](https://bbs.archlinux.org/viewtopic.php?id=134892)

---

### Post by jdefed on 2014-03-20
I am using optical out to receiver. The .pulse-default-sink file shows analog stereo as output. Does that need to be changed and how to do it?

---

### Post by jdefed on 2014-03-20
I have everything working now. To get audio I installed pulseaudio volume control, which allowed me to set digital audio out through spdif. That also set .pulse-default-sink to digital out.

thank you
jim d

---

