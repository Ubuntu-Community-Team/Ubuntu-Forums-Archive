---
title: "Please Confirm These Bugs"
date: 2008-08-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-08-13
Hi folks :) Would someone please confirm the following bugs in Launchpad that I have reported by moving the bug status to confirmed and adding a related comment:

1. NTPD In 32bit Legacy Mode on x64 Install - basically my 64bit install is running the network time daemon in 32bit mode when it shouldnt be.

[https://bugs.launchpad.net/ubuntu/+source/openntpd/+bug/244133](https://bugs.launchpad.net/ubuntu/+source/openntpd/+bug/244133)

2. Totem Fails On Multiple Audio and Subtitle Streams - Movie player doesnt switch subtitle and or audio streams properly when playing back footage with these.

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/255929](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/255929)

3. Grub Installs To Wrong Root Path - this is a nasty production bug where in specific configurations Ubuntu fails to set the right grub root path and will not boot without non intuitive user intervention to correct it. Ronacc kindly attached some logs, thanks Ronacc.

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/243803](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/243803)

---

### Post by ronacc on 2008-08-13
I'm not seeing the NTPD bug here , atleast I'm not geting any mesages about it in my logs , and I can't find the samples on the mplayer ftp site you mention in the mplayer bug report to test that one .

---

### Post by Nullack on 2008-08-13
Heres a file ~6mb

[http://samples.mplayerhq.hu/MPEG-4/embedded_subs/1Video_2Audio_2SUBs_timed_text_streams_.mp4](http://samples.mplayerhq.hu/MPEG-4/embedded_subs/1Video_2Audio_2SUBs_timed_text_streams_.mp4)

Ill look into the NTPD bug, if you could confirm the totem one and the grub root that would be great. Thanks Ronacc

---

### Post by ronacc on 2008-08-13
tried the mp4 , I can't get any subtitles at all . I'll look into that later . Posting my log is the best I can do about the grub thing because I I only let the first install on my box install grub and just manualy add boot stanzas after that . Gina may be able to help with it I think he has a thread in here someplace about the same thing.BTW I have never had much luck with ubuntu's grub installer getting things right , thats one of the reasons I do things the way I do:)

---

### Post by InfinityCircuit on 2008-08-13
I have confirmed the grub bug.  It also requires editing the swap partition in /etc/initramfs-tools/conf.d/resume or usplash doesn't work.

---

### Post by OutOfReach on 2008-08-13
Odd, I haven't had any of these bugs.

---

### Post by ronacc on 2008-08-13
i must be missing something , when I play the mp4 you pointed me at selecting view>subtitles says empty , I also d'ld another video that has a seperate txt sutitle file but that one shows empty also ? are there additional debs I need to add to get subtitles ?

---

### Post by Nullack on 2008-08-14
@InfinityCircuit - many thanks

@out of reach - you do have the totem bug you just havent noticed it yet :) The grub one is specific to certain hardware configurations and the NTP daemon bug on 64bit Im looking at more closely.

@Ronacc, sorry perhaps that was not the best sample file to supply. Im pretty sure that gstreamer doesnt support timed text subtitles. Im not sure about external subtitle support in gstreamer either. These things I am researching and testing currently before submitting bugs. Anyway to test how the stream switching is broken change the audio track in that tron sample I provided and observe that english continues. The only way is to change the preferred audio track and then use the left mouse button to click on a prior section of playback to reset the streams manually.

---

### Post by Nullack on 2008-08-14
Heres a multiple sub sample in MKV that does work with gstreamer: ~7MB

[http://samples.mplayerhq.hu/Matroska/subtitles/multiple_sub_sample.mkv](http://samples.mplayerhq.hu/Matroska/subtitles/multiple_sub_sample.mkv)

Note, the good, bad and ugly plugins and the ffmpeg plugin for gstreamer are more or less required for most video testing. :)

---

### Post by ronacc on 2008-08-14
I confirmed the totem bug . I always install the good,bad and ugly codecs along with every other one I can find , infact it was installing the codecs from mpalyerhq.hu that I first bumped into the root nautilus changing the permissions on / :)

---

### Post by Nullack on 2008-08-14
Thanks Ronacc, can you please move the status of the bug from new to confirmed. Folk get upset if I do it as the bug originator understandably :)

---

### Post by ronacc on 2008-08-14
done

---

