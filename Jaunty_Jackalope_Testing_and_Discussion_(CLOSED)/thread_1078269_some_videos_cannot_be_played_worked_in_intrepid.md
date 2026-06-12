---
title: "some videos cannot be played worked in intrepid"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2009-02-23
so i upgraded to jaunty toaday and i am not able to play some videos which i could play in totem in intrepid

like

*.mkv files
files using h264 codec etc

they **played in intrepid** in totem before the upgrade.

I ADDED medibuntu repos for jaunty, reinstalled gstreamer plugins still no use.

when i click to open a file with .mkv type then totem opens then after2-3 secs closes.

also **some** not all **avi video files are giving stuttering** problems.

**they all work in mplayer**

what do i do?

---

### Post by Nullack on 2009-02-23
Host some samples online so we can look please. The container type such as avi or mkv tells little detail of the streams inside the container.

---

### Post by tgpraveen on 2009-02-23
well the icons for these files dont give a preview shot of the video file.
and when i click on properties by right clicking on these files nautilius just crashes

---

### Post by taavikko on 2009-02-23
> **tgpraveen said:**
> well the icons for these files dont give a preview shot of the video file.
and when i click on properties by right clicking on these files nautilius just crashes

Info can be attained by cli
```
file video.avi
```

---

### Post by Nullack on 2009-02-23
Use tools like mencoder and mkvnix to strip em into small samples

---

### Post by philinux on 2009-02-23
Totem just got an update. It fixed my wmv problem.

---

### Post by terry_gardener on 2009-02-23
i am also getting the same problem as tgpraveen with mkv files. 

i can play them with vlc but not totem as it crashes, cant even right properties as it crashes nautilus. 

i have played them in vlc to get the codec info which is as follows. 

video= avc1 
audio = mpga 

any further info just let me know. 

i am currently doing the update so will check afterwards.

---

### Post by philinux on 2009-02-23
I got my problem back so I tried uninstalling totem-gstreamer and installing totem-xine. Now I can play wmv files. But right clicking and selecting properties crashes nautilus.

---

### Post by terry_gardener on 2009-02-23
i have finished the update and rebooted and retried and get exactly the same problem. 

i have checked the syslog and it says the following.

terry-desktop kernel: [   68.576720] totem[4085]: segfault at ab36000 ip b7105377 sp b310a828 error 6 in libc-2.9.so[b708c000+15c000]
terry-desktop kernel: [  122.168247] nautilus[4135]: segfault at aac1000 ip b7309377 sp b6be1838 error 6 in libc-2.9.so[b7290000+15c000]

don't know if this helps.

---

### Post by tgpraveen on 2009-02-24
is there any one who can play .mkv or .mp4 files using totem?
are u using medibuntu?
which version of gstreamer u have installed?

---

### Post by Nullack on 2009-02-24
> **tgpraveen said:**
> is there any one who can play .mkv or .mp4 files using totem?
are u using medibuntu?
which version of gstreamer u have installed?

yes
No
latest as per main repos

Good, bad, ugly, multiverse ugly nd bad, ffmpeg gstreamer plugins

---

### Post by tgpraveen on 2009-02-24
damnit this is really frustrating now. i have all gstreamer installed. i have medibuntu installed too. still cant do it. while it worked perfectly on intrepid.

could someone else with this problem  think of what else might be wrong?

i did have medibuntu enabled on intrepid then moved to jaunty. had these problems. then enabled medibuntu repos for jaunty and then also have this problem.

---

### Post by ADINSX on 2009-02-25
I've been having the same problem. Videos with h.264 encoding crash Totem. I can still play .mkv's (and other container formats) if the video codec is something other than h.264. I have all of the gstreamer plugins installed, still have the same problem.

mplayer plays the videos fine.

---

### Post by Nullack on 2009-02-25
Samples please :)

---

### Post by terry_gardener on 2009-02-26
i have uploaded a sample mkv file.

[http://homepage.ntlworld.com/terry.gardener/test.mkv](http://homepage.ntlworld.com/terry.gardener/test.mkv)

please can you have a look at this and see if it works for you in totem. 

thanks

---

### Post by taavikko on 2009-02-26
> **terry_gardener said:**
> i have uploaded a sample mkv file.

[http://homepage.ntlworld.com/terry.gardener/test.mkv](http://homepage.ntlworld.com/terry.gardener/test.mkv)

please can you have a look at this and see if it works for you in totem. 

thanks


Output:
```
totem Public/test.mkv 
*** glibc detected *** totem: realloc(): invalid pointer: 0x0000000004545380 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f4a094cacb8]
/lib/libc.so.6(realloc+0x2bc)[0x7f4a094cff3c]
/usr/lib/libavcodec.so.52(av_fast_realloc+0x29)[0x7f49ef8d3489]
/usr/lib/libavcodec.so.52(ff_vdpau_add_data_chunk+0x4f)[0x7f49efa641af]
/usr/lib/libavcodec.so.52[0x7f49efa57d67]
/usr/lib/libavcodec.so.52[0x7f49efa59098]
/usr/lib/libavcodec.so.52(avcodec_decode_video+0xbb)[0x7f49ef8d1b8b]
/usr/lib/gstreamer-0.10/libgstffmpeg.so[0x7f49f0429bcb]
/usr/lib/gstreamer-0.10/libgstffmpeg.so[0x7f49f042bc80]
/usr/lib/libgstreamer-0.10.so.0[0x7f4a0ea21f76]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x353)[0x7f4a0ea23253]
/usr/lib/gstreamer-0.10/libgstcoreelements.so[0x7f49ff90c832]
/usr/lib/libgstreamer-0.10.so.0[0x7f4a0ea42d86]
/usr/lib/libglib-2.0.so.0[0x7f4a0a1461d7]
/usr/lib/libglib-2.0.so.0[0x7f4a0a144c74]
/lib/libpthread.so.0[0x7f4a0d4633ba]
/lib/libc.so.6(clone+0x6d)[0x7f4a09538fcd]
======= Memory map: ========
00400000-0046d000 r-xp 00000000 08:01 45263                              /usr/bin/totem-gstreamer
0066d000-0066f000 r--p 0006d000 08:01 45263                              /usr/bin/totem-gstreamer
0066f000-00673000 rw-p 0006f000 08:01 45263                              /usr/bin/totem-gstreamer
02374000-047c4000 rw-p 02374000 00:00 0                                  [heap]
7f49e7de8000-7f49e7dfe000 r-xp 00000000 08:01 67774                      /lib/libgcc_s.so.1
7f49e7dfe000-7f49e7ffe000 ---p 00016000 08:01 67774                      /lib/libgcc_s.so.1
7f49e7ffe000-7f49e7fff000 r--p 00016000 08:01 67774                      /lib/libgcc_s.so.1
7f49e7fff000-7f49e8000000 rw-p 00017000 08:01 67774                      /lib/libgcc_s.so.1
7f49e8000000-7f49e8021000 rw-p 7f49e8000000 00:00 0 
7f49e8021000-7f49ec000000 ---p 7f49e8021000 00:00 0 
7f49ec02e000-7f49ec042000 r-xp 00000000 08:01 120343                     /usr/lib/libid3tag.so.0.3.0
7f49ec042000-7f49ec241000 ---p 00014000 08:01 120343                     /usr/lib/libid3tag.so.0.3.0
7f49ec241000-7f49ec244000 rw-p 00013000 08:01 120343                     /usr/lib/libid3tag.so.0.3.0
7f49ec244000-7f49ec262000 r-xp 00000000 08:01 120353                     /usr/lib/libmad.so.0.2.1
7f49ec262000-7f49ec462000 ---p 0001e000 08:01 120353                     /usr/lib/libmad.so.0.2.1
7f49ec462000-7f49ec463000 r--p 0001e000 08:01 120353                     /usr/lib/libmad.so.0.2.1
7f49ec463000-7f49ec464000 rw-p 0001f000 08:01 120353                     /usr/lib/libmad.so.0.2.1
7f49ec464000-7f49ec474000 r-xp 00000000 08:01 87145                      /usr/lib/gstreamer-0.10/libgstmad.so
7f49ec474000-7f49ec673000 ---p 00010000 08:01 87145                      /usr/lib/gstreamer-0.10/libgstmad.so
7f49ec673000-7f49ec674000 r--p 0000f000 08:01 87145                      /usr/lib/gstreamer-0.10/libgstmad.so
7f49ec674000-7f49ec675000 rw-p 00010000 08:01 87145                      /usr/lib/gstreamer-0.10/libgstmad.so
7f49ec675000-7f49ec676000 ---p 7f49ec675000 00:00 0 
7f49ec676000-7f49ece76000 rwxp 7f49ec676000 00:00 0 
7f49ece76000-7f49ece82000 r-xp 00000000 08:01 87147                      /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
7f49ece82000-7f49ed082000 ---p 0000c000 08:01 87147                      /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
7f49ed082000-7f49ed083000 r--p 0000c000 08:01 87147                      /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
7f49ed083000-7f49ed084000 rw-p 0000d000 08:01 87147                      /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
7f49ed084000-7f49ed085000 ---p 7f49ed084000 00:00 0 
7f49ed085000-7f49ed885000 rwxp 7f49ed085000 00:00 0 
7f49ed885000-7f49edc46000 rw-p 7f49ed885000 00:00 0 
7f49edc46000-7f49edcc3000 r-xp 00000000 08:01 119769                     /usr/lib/libxvidcore.so.4.1
7f49edcc3000-7f49edec2000 ---p 0007d000 08:01 119769                     /usr/lib/libxvidcore.so.4.1
7f49edec2000-7f49edecd000 rw-p 0007c000 08:01 119769                     /usr/lib/libxvidcore.so.4.1
7f49edecd000-7f49edf37000 rw-p 7f49edecd000 00:00 0 
7f49edf37000-7f49edfc4000 r-xp 00000000 08:01 119756                     /usr/lib/libx264.so.65
7f49edfc4000-7f49ee1c3000 ---p 0008d000 08:01 119756                     /usr/lib/libx264.so.65
7f49ee1c3000-7f49ee1c5000 r--p 0008c000 08:01 119756                     /usr/lib/libx264.so.65
7f49ee1c5000-7f49ee1c6000 rw-p 0008e000 08:01 119756                     /usr/lib/libx264.so.65
7f49ee1c6000-7f49ee1c9000 rw-p 7f49ee1c6000 00:00 0 
7f49ee1c9000-7f49ee1e3000 r-xp 00000000 08:01 36402                      /usr/lib/libvorbisenc.so.2.0.3
7f49ee1e3000-7f49ee3e2000 ---p 0001a000 08:01 36402                      /usr/lib/libvorbisenc.so.2.0.3
7f49ee3e2000-7f49ee3e3000 r--p 00019000 08:01 36402                      /usr/lib/libvorbisenc.so.2.0.3
7f49ee3e3000-7f49ee5a2000 rw-p 0001a000 08:01 36402                      /usr/lib/libvorbisenc.so.2.0.3
7f49ee5a2000-7f49ee5e8000 r-xp 00000000 08:01 24620                      /usr/lib/libtheora.so.0.3.3
7f49ee5e8000-7f49ee7e7000 ---p 00046000 08:01 24620                      /usr/lib/libtheora.so.0.3.3
7f49ee7e7000-7f49ee7e9000 rw-p 00045000 08:01 24620                      /usr/lib/libtheora.so.0.3.3
7f49ee7e9000-7f49ee801000 r-xp 00000000 08:01 24526                      /usr/lib/libspeex.so.1.5.0
7f49ee801000-7f49eea01000 ---p 00018000 08:01 24526                      /usr/lib/libspeex.so.1.5.0
7f49eea01000-7f49eea02000 r--p 00018000 08:01 24526                      /usr/lib/libspeex.so.1.5.0
7f49eea02000-7f49eea03000 rw-p 00019000 08:01 24526                      /usr/lib/libspeex.so.1.5.0
7f49eea03000-7f49eea75000 r-xp 00000000 08:01 75687                      /usr/lib/libschroedinger-1.0.so.0.1.0
7f49eea75000-7f49eec74000 ---p 00072000 08:01 75687                      /usr/lib/libschroedinger-1.0.so.0.1.0
7f49eec74000-7f49eec75000 r--p 00071000 08:01 75687                      /usr/lib/libschroedinger-1.0.so.0.1.0
7f49eec75000-7f49eec77000 rw-p 00072000 08:01 75687                      /usr/lib/libschroedinger-1.0.so.0.1.0
7f49eec77000-7f49eecbd000 r-xp 00000000 08:01 119743                     /usr/lib/libmp3lame.so.0.0.0
7f49eecbd000-7f49eeebd000 ---p 00046000 08:01 119743                     /usr/lib/libmp3lame.so.0.0.0
7f49eeebd000-7f49eeebe000 r--p 00046000 08:01 119743                     /usr/lib/libmp3lame.so.0.0.0
7f49eeebe000-7f49eeebf000 rw-p 00047000 08:01 119743                     /usr/lib/libmp3lame.so.0.0.0
7f49eeebf000-7f49eeef0000 rw-p 7f49eeebf000 00:00 0 
7f49eeef0000-7f49eeefd000 r-xp 00000000 08:01 61407                      /usr/lib/libgsm.so.1.0.12
7f49eeefd000-7f49ef0fc000 ---p 0000d000 08:01 61407                      /usr/lib/libgsm.so.1.0.12
7f49ef0fc000-7f49ef0fd000 rw-p 0000c000 08:01 61407                      /usr/lib/libgsm.so.1.0.12
7f49ef0fd000-7f49ef13a000 r-xp 00000000 08:01 119726                     /usr/lib/libfaad.so.0.0.0
7f49ef13a000-7f49ef339000 ---p 0003d000 08:01 119726                     /usr/lib/libfaad.so.0.0.0
7f49ef339000-7f49ef33a000 r--p 0003c000 08:01 119726                     /usr/lib/libfaad.so.0.0.0
7f49ef33a000-7f49ef33d000 rw-p 0003d000 08:01 119726                     /usr/lib/libfaad.so.0.0.0
7f49ef33d000-7f49ef34c000 r-xp 00000000 08:01 119709                     /usr/lib/libfaac.so.0.0.0
7f49ef34c000-7f49ef54b000 ---p 0000f000 08:01 119709                     /usr/lib/libfaac.so.0.0.0
7f49ef54b000-7f49ef54c000 r--p 0000e000 08:01 119709                     /usr/lib/libfaac.so.0.0.0
7f49ef54c000-7f49ef54f000 rw-p 0000f000 08:01 119709                     /usr/lib/libfaac.so.0.0.0
7f49ef54f000-7f49ef5ec000 r-xp 00000000 08:01 119799                     /usr/lib/libavformat.so.52.25.0
7f49ef5ec000-7f49ef7eb000 ---p 0009d000 08:01 119799                     /usr/lib/libavformat.so.52.25.0
7f49ef7eb000-7f49ef7ef000 r--p 0009c000 08:01 119799                     /usr/lib/libavformat.so.52.25.0
7f49ef7ef000-7f49ef7f7000 rw-p 000a0000 08:01 119799                     /usr/lib/libavformat.so.52.25.0
7f49ef7f7000-7f49ef843000 rw-p 7f49ef7f7000 00:00 0 
7f49ef843000-7f49efcdd000 r-xp 00000000 08:01 119781                     /usr/lib/libavcodec.so.52.11.0
7f49efcdd000-7f49efedc000 ---p 0049a000 08:01 119781                     /usr/lib/libavcodec.so.52.11.0
7f49efedc000-7f49efee6000 r--p 00499000 08:01 119781                     /usr/lib/libavcodec.so.52.11.0
7f49efee6000-7f49efef3000 rw-p 004a3000 08:01 119781                     /usr/lib/libavcodec.so.52.11.0
7f49efef3000-7f49f0204000 rw-p 7f49efef3000 00:00 0 
7f49f0204000-7f49f020f000 r-xp 00000000 08:01 119689                     /usr/lib/libavutil.so.49.14.0
7f49f020f000-7f49f040e000 ---p 0000b000 08:01 119689                     /usr/lib/libavutil.so.49.14.0
7f49f040e000-7f49f040f000 r--p 0000a000 08:01 119689                     /usr/lib/libavutil.so.49.14.0
7f49f040f000-7f49f0410000 rw-p 0000b000 08:01 119689                     /usr/lib/libavutil.so.49.14.0
7f49f0410000-7f49f0413000 rw-p 7f49f0410000 00:00 0 
7f49f0413000-7f49f0440000 r-xp 00000000 08:01 119849                     /usr/lib/gstreamer-0.10/libgstffSegmentation fault (core dumped)
```

---

### Post by terry_gardener on 2009-02-26
so does this output mean it worked for you. 

if so what packages do you have so i can compare 

thanks

---

### Post by taavikko on 2009-02-26
> **terry_gardener said:**
> so does this output mean it worked for you. 

if so what packages do you have so i can compare 

thanks

No, it didn't work.

Very last line "segfault, core dumped"

---

### Post by terry_gardener on 2009-02-27
i have raised  a bug report with regard to this 

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/335595](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/335595)

---

### Post by Nullack on 2009-02-28
On my jaunty build, I cannot replicate. The test sample plays fine on gstreamer/totem, no seg fault.

---

### Post by thiebaude on 2009-02-28
Did you install the w32 codecs, also.

---

### Post by tgpraveen on 2009-02-28
^^yes from medibuntu jaunty repos

---

### Post by tgpraveen on 2009-03-07
this problem still exists . man this is probably the most irritating problem of jaunty right now.
any word of related bug report or ppl working on it?

---

### Post by terry_gardener on 2009-03-09
to resolve this issue remove the libavcodec unstripped package and it dependencies and then open the file it will search for codecs and properly find the correct correct and download it for you, after which it works. 

you will need to reinstall vlc and vlc-nox packages again as libavcodec unstripped removes them. 

i turned my bug report into a question and it is now solved. 

[https://answers.launchpad.net/ubuntu/+source/ffmpeg-debian/+question/63621](https://answers.launchpad.net/ubuntu/+source/ffmpeg-debian/+question/63621)

hope this helps.

---

