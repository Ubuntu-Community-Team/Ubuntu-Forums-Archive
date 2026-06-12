---
title: "Heads-up regarding PulseAudio in Jaunty"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crimsun on 2009-03-02
Please see [http://ubuntuforums.org/showpost.php?p=6825748&postcount=5](http://ubuntuforums.org/showpost.php?p=6825748&postcount=5) regarding current PulseAudio integration issues.

---

### Post by plun on 2009-03-02
Hi

Just a question.....

audio settings management (alsa-utils) is disabled now (checked 2 PCs)

Menu System>> administration >> services

Should it be so ?

---

### Post by crimsun on 2009-03-02
Yes, it should be shown as disabled. The /etc/init.d/alsa-utils script is invoked via a udev rule. You should **not** invoke the initscript explicitly in a runlevel with the start argument.

---

### Post by plun on 2009-03-02
> **crimsun said:**
> Yes, it should be shown as disabled. The /etc/init.d/alsa-utils script is invoked via a udev rule. You should **not** invoke the initscript explicitly in a runlevel with the start argument.

Thanks for answer ! 

Maybe a bug against this entry :confused:

---

### Post by crimsun on 2009-03-02
The initscript correctly exists in its current directory.

---

### Post by Taiebot65 on 2009-03-05
Rhythmbox is not working with pulseaudio shall i report it as a bug?
If i kill pulse audio it s working without any issues

---

### Post by crimsun on 2009-03-05
> **Taiebot65 said:**
> Rhythmbox is not working with pulseaudio shall i report it as a bug?
If i kill pulse audio it s working without any issues

Yes, please report the bug *if reproducible using my PPA package*.

Please also read [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-March/007305.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-March/007305.html) for a summary of outstanding Jaunty issues.

You may also find [https://bugs.launchpad.net/bugs/334319](https://bugs.launchpad.net/bugs/334319) relevant.

---

### Post by Taiebot65 on 2009-03-05
I have to say only rhythmbox is causing issues i ve got choppy sound at the beginning of others sounds applications but after 10 sec. my sound is correct.

I can not find your ppa.

---

### Post by rudenko_ruslan on 2009-03-05
> **Taiebot65 said:**
> I can not find your ppa.
[https://launchpad.net/~crimsun/+archive/ppa](https://launchpad.net/~crimsun/+archive/ppa)

---

### Post by Taiebot65 on 2009-03-05
Ok i remenber now it's maybe not a bug....I was testing the other day my USB sound card and i changed the playback stream output for rhythmbox to RTP Muticast sink..
That's why i ve disconnected my USB sound card and i had not the correct ouput. Took me two days to find out...

---

### Post by crimsun on 2009-03-05
Today's PulseAudio status refresh: [http://identi.ca/notice/2630222](http://identi.ca/notice/2630222)

---

### Post by ace214 on 2009-03-07
I discovered last night that my built-in microphone won't pick up sound anymore. I used it as recently as last Tuesday. A line-in mic works fine.

Might this be related to these changes? I updated to your latest PPA package. My sound card is Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04).

EDIT: Actually, it doesn't seem to be working under Windows now either... Guess I've got a very recent hardware problem.

---

### Post by crimsun on 2009-03-09
Ok folks, ubuntu11~ppa8 (in [my PPA]("https://launchpad.net/~crimsun/+archive/ppa")) is ready for Alpha 6 and will be in Jaunty RSN. *(EDIT: ubuntu11 has been uploaded to Jaunty.)* The list of changes is fairly lengthy:

  * Reenable 0030_set_tsched0.patch, which re-disables glitch-free;
    too many users are reporting regressions and audio aberrations.
  * Adjust 0003_change_resample_and_buffering.patch to use linear
    resampler to work better with lack of PREEMPT in jaunty's
    -generic kernel config (LP: #207135, #322250, #332761, #335955,
    LP: #336965).
  * Last upload, specifically 0091_workaround_alsa_horkage, fixes:
    LP: #235990, #237443, #279847, #317997, #323185, #330814,
    LP: #334874.
  * sudo -H change in ubuntu6 fixed LP: #312505.
  * Closing old bugs fixed in 0.9.11+: LP: #187963, #193520, #211052.
  * Refresh 0006_regen-autotools.patch.
  * Add 0043_load_sample_dir_lazy.patch to cache
    /usr/share/sounds/ubuntu/stereo/* in default.pa.
  * debian/:
    - control: Build against libcap2-dev (LP: #339448);
    - copyright: Update copyright from Debian's 0.9.14-2;
    - rules: Add DEB_OPT_FLAG = -O3 as per recommendation from
      pulseaudio-discuss/2007-December/001017.html.
  * Refresh fixes from git HEAD:
    - 0038_handle_errno_properly.patch,
    - 0091_workaround_alsa_horkage.patch,
    - 0092_fix_null_pointer_access.patch.

Note that glitch-free is again **dis**abled by default. If you are one of the few lucky users whose system actually performs better (e.g., fewer audio aberrations) with it enabled, then you will be pleased to note that I've worked pretty extensively this past weekend to isolate the problematic changesets causing PA to take too long to settle.

---

### Post by Benjamin_Lebsanft on 2009-03-09
This problem existed since Intrepid. I've got a asus board with integrated realtek 883 chip and when using the pulseaudio mixer, the volume only changes in the lowest 20% of the slider. Is there a workaround?

When using alsa mixer master doesn't change the volume at all and when using the pcm slider i get crackling when muting or setting to zero.

---

### Post by taavikko on 2009-03-13
Anyone else experiencing crackle in sounds?

Sometimes after pause in rhythmbox( songs are played at accelerated speeds, and sound is just cosmic noise, reminds of old dial-up sound)

Even on flash-content in browser is affected, so pretty much occasional problem. Cracke disappears, when restarting affected app.

---

### Post by mattisking on 2009-03-14
I just noticed this today. I'm getting some crackling, and I'm also getting a low hum feedback sound in my speakers whenever I move the mouse.

---

### Post by taavikko on 2009-03-14
tail -15 /var/log/user.log
```
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410826272 bytes (418282907921 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410811936 bytes (418282907840 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410797600 bytes (418282907759 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410783264 bytes (418282907677 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410783360 bytes (418282907678 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410769024 bytes (418282907597 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410754688 bytes (418282907515 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410740352 bytes (418282907434 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410726016 bytes (418282907353 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410711680 bytes (418282907272 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410697344 bytes (418282907190 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410683008 bytes (418282907109 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410668672 bytes (418282907028 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410654336 bytes (418282906947 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410640000 bytes (418282906865 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
```

Whole log-file is flooded with these, Probably the "fix-committed"
in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330814)
Should solve this issue?

---

### Post by lamborghiniwang on 2009-03-14
> **taavikko said:**
> tail -15 /var/log/user.log
```
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410826272 bytes (418282907921 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410811936 bytes (418282907840 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410797600 bytes (418282907759 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410783264 bytes (418282907677 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410783360 bytes (418282907678 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410769024 bytes (418282907597 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410754688 bytes (418282907515 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410740352 bytes (418282907434 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410726016 bytes (418282907353 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410711680 bytes (418282907272 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410697344 bytes (418282907190 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410683008 bytes (418282907109 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410668672 bytes (418282907028 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410654336 bytes (418282906947 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
Mar 14 09:31:46 elite pulseaudio[4017]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053410640000 bytes (418282906865 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.
```

Whole log-file is flooded with these, Probably the "fix-committed"
in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330814)
Should solve this issue?

same problem here. Huge log file, cracks in audio out. When using PluseAudio as the audio out device in Skype, huge lag with Skype using 100% CPU.

---

### Post by eluminx on 2009-03-14
Does anyone have sound in flash working with PA 0.9.15?  Seems like everything is working for me, except sound with flash.  Is like being back in the days of intrepid testing all over again...

---

### Post by lamborghiniwang on 2009-03-14
> **eluminx said:**
> Does anyone have sound in flash working with PA 0.9.15?  Seems like everything is working for me, except sound with flash.  Is like being back in the days of intrepid testing all over again...

The sound in flash works fine for me. 64-bit Jaunty with both 64-bit and 32-bit flash player.

---

### Post by eluminx on 2009-03-14
I have no idea why it doesnt work for me on 64bit Jaunty.  I tried flash from the repos and tried dl the 64bit version from adobe.com and none have worked.

---

### Post by Ng Oon-Ee on 2009-03-14
My log file fills up with "snd_pcm_avail_update() returned a value that is exceptionally large" messages too. 32-bit Jaunty, latest updates applied, no git pulse though.

---

### Post by markbuntu on 2009-03-14
The latest update seems to have fixed something? 

the playback volume bar now follows the music when using simultaneous output. 

My usb headset is not scratchy if pavucontrol is open??? Sounds fine as long as I keep pavucontrol open, even minimized but as soon as i close it the usb gets scratchy within a minute. The second i open pavucontrol it stops. This happens with the stream directed to usb or simultaneous.

usb volume still cuts out completly at 54% (alsa regression?). 

I still can't move the system sounds. Is this a bug or a feature?

I don't know if i have the time or inclination to file all the bug reports...

---

### Post by crimsun on 2009-03-16
> **taavikko said:**
> Whole log-file is flooded with these, Probably the "fix-committed"
in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330814)
Should solve this issue?

(The Linux fix) is an experimental one. I've lessened the verboseness of the logging for that error since we already know the root cause.

The syslog DoS is fixed in 0.9.14-0ubuntu12.

---

### Post by ianc on 2009-03-16
crimsun - for sure it's me being brainless as usual, but I just want to check that there's no reason your end for this (error message after I add your ppa in Software Sources):

```
Failed to fetch http://ppa.launchpad.net/crimsun/ppa/ubuntu/dists/jaunty/Release  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Any suggestions as to something obvious I'm doing wrong?

Thanks
Ian

---

### Post by crimsun on 2009-03-16
> **ianc said:**
> Any suggestions as to something obvious I'm doing wrong?

There's currently nothing in my PPA, because what was in it (pulseaudio_0.9.14-0ubuntu12~crimsun1) has been superceded by what's currently in jaunty (pulseaudio_0.9.14-0ubuntu12).

I track changes very closely and tend to delete binary packages from my PPA as soon as the source package upload in jaunty has been accepted by soyuz.

---

### Post by ianc on 2009-03-17
That would of course explain a lot - although unfortunately not the audio problems I'm having at the moment! I'll have to find another way to try to fix those...

Thanks
Ian

---

### Post by Taiebot65 on 2009-03-18
What about cpu usage with pulse audio. Just listening music with rhythmbox eats me 10 to 15% of cpu. I remenber in gutsy reaching the maximum limit of 4% when i was listening to music..Is it normal?

---

### Post by Taiebot65 on 2009-03-18
I have maybe over exaggerated about cpu usage i think 8 to 12% will be more accurate but it s still double than what i had before..Is it because i stream my music over an other device?

---

### Post by crimsun on 2009-03-18
> **Taiebot65 said:**
> I have maybe over exaggerated about cpu usage i think 8 to 12% will be more accurate but it s still double than what i had before..Is it because i stream my music over an other device?

Streaming over a network is known to cause high cpu utilisation, yes.

You could try experimenting with the resampling algorithm (see /etc/pulse/daemon.conf).

---

### Post by stoffe on 2009-03-19
> **taavikko said:**
> Anyone else experiencing crackle in sounds?

Sometimes after pause in rhythmbox( songs are played at accelerated speeds, and sound is just cosmic noise, reminds of old dial-up sound)

Even on flash-content in browser is affected, so pretty much occasional problem. Cracke disappears, when restarting affected app.

I have crackling as well, especially (it seems) when there has been no sound for a while, which has led me to believe that the sound card "wakes up" abruptly with full volume, or something like that. Had to disable sound in pidgin, because with every happening it would crackle, but also playing youtube videos and other stuff would do the same thing.

---

### Post by crimsun on 2009-03-19
> **stoffe said:**
> I have crackling as well, especially (it seems) when there has been no sound for a while, which has led me to believe that the sound card "wakes up" abruptly with full volume, or something like that. Had to disable sound in pidgin, because with every happening it would crackle, but also playing youtube videos and other stuff would do the same thing.

Try adding:

options snd-hda-intel power_save_controller=1

to /etc/modprobe.d/alsa-base.conf

and rebooting.

---

### Post by stoffe on 2009-03-19
> **crimsun said:**
> Try adding:

options snd-hda-intel power_save_controller=1

to /etc/modprobe.d/alsa-base.conf

and rebooting.

Didn't make any difference. Any other things I could try?

---

### Post by stoffe on 2009-03-19
Also noticing now, that the sound crackling/static may be more random than just after a pause. Playback itself also seems flakey and/or related, a bit hit and miss.

---

### Post by andrewabc on 2009-03-19
I've had crackling etc on both windows and ubuntu for 2 years. It is random for me.
It may be speakers or the sound card. I think it was worse on my old cheap speakers than my current surround speakers, but it still shows up.

I have realtek sound card.

---

### Post by crimsun on 2009-03-19
> **stoffe said:**
> Didn't make any difference. Any other things I could try?

File a bug report affecting the linux source package. *It is absolutely essential that you attach the output from the [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) script.*

---

### Post by jmmL on 2009-03-19
This scratching issue is also affecting me. Here is my output of *alsa-info.sh*: [http://www.alsa-project.org/db/?f=44dc1549d60508bd181a03ee1c65465aa5c9024d](http://www.alsa-project.org/db/?f=44dc1549d60508bd181a03ee1c65465aa5c9024d)

Where do I need to send this information to be of any help?

---

### Post by crimsun on 2009-03-19
> **jmmL said:**
> This scratching issue is also affecting me. Here is my output of *alsa-info.sh*: [http://www.alsa-project.org/db/?f=44dc1549d60508bd181a03ee1c65465aa5c9024d](http://www.alsa-project.org/db/?f=44dc1549d60508bd181a03ee1c65465aa5c9024d)

Where do I need to send this information to be of any help?

Again, file a bug affecting the `linux' source package, and remember to attach the URL of that output.

---

### Post by jmmL on 2009-03-19
As suggested, I have filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

Have I missed out any useful information?

---

### Post by ssc351 on 2009-03-19
anyone have any problems with the sound being super quiet?  My sound works and the volume meter makes it louder and quieter, but it off by like a scale of 10.  It sounds fine, no crackling, etc...but I need to have my ear against the speaker with the volume all the way up to hear it.

I am running 64bit..I installed the gnome-alsamixer as suggested by another post by no luck.

---

### Post by crimsun on 2009-03-20
Please see [this blog post]("http://drowninginbugs.blogspot.com/2009/03/call-for-testers-jaunty-64-bit.html").

---

### Post by smbm on 2009-03-21
I have installed it on my 64bit install, it seems to be fine.

What changes have you made?

---

### Post by vishalrao on 2009-03-21
I think this is the change: [http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commitdiff;h=ed3da3d9a0ef13c6fe1414ec73c9c1be12747b62](http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commitdiff;h=ed3da3d9a0ef13c6fe1414ec73c9c1be12747b62)

---

### Post by vishalrao on 2009-03-22
Just tried the crimsun/dtchen kernel with hw_ptr changes and pulseaudio working smooth! on my desktop with intel DP35DP mobo (onboard intel hda sound) - will also try on my tablet PC and reply to the list email/post alsa-info in the bug...

---

### Post by LittleKoy on 2009-03-22
I just updated from Intrepid to Jaunty.
I played a video (h264) using totem and worked good (noticeable less cpu usage), but after about 6 minutes pulseaudio went rampage, it sucked the whole cpu, the sound died while the video began fast-forwarding, and in the end totem crashed.

Edit: it happens only with totem. Using MPlayer the whole video played fine.

---

### Post by scaine on 2009-03-22
I'm trying to find a tool I used a couple of months ago which I thought I launched from the volume-applet.  It gave me incredibly fine-grained control over the "boost" settings of my in-built microphone on my laptop, by using pulseaudio.  I could make the built-in mic hypersensitive, which was perfect for Skype.

Anyone know where that went, or if it's still available somewhere?

---

### Post by ktp on 2009-03-22
Are you talking about the new gnome volumn control, which is removed from default ubuntu install?

You can install it: gnome-volume-control-pulse

---

### Post by LittleKoy on 2009-03-23
No sound anymore this morning! Yesterday everything was fine, but when I turned on the pc this morning, it was completely mute!

Edit: ah ah, nevermind, for some strange reason my master volume was turned off... :D

---

### Post by andrewabc on 2009-03-23
> **LittleKoy said:**
> No sound anymore this morning! Yesterday everything was fine, but when I turned on the pc this morning, it was completely mute!

Edit: ah ah, nevermind, for some strange reason my master volume was turned off... :D

There is a thread created specifically for that bug. Should be on the first couple pages of this board. If you can figure anything out please help, many are having it.

EDIT:
[Strange volume control problem...](http://ubuntuforums.org/showthread.php?t=1101902)

---

### Post by Nixie Pixel on 2009-03-24
I believe my pulse audio somehow broke completely a couple of days ago, likely due to a kernel update.  I now get only crackling noises, no sound at all, no matter what I do, or what I try to play.

I have seen notes regarding crackling above, but only with other sounds, not en lieu of them.  Does anyone know what having no sound at all, only crackling, might mean?

Thanks!

---

### Post by taavikko on 2009-03-24
> **Nixie Pixel said:**
> I believe my pulse audio somehow broke completely a couple of days ago, likely due to a kernel update.  I now get only crackling noises, no sound at all, no matter what I do, or what I try to play.

I have seen notes regarding crackling above, but only with other sounds, not en lieu of them.  Does anyone know what having no sound at all, only crackling, might mean?

Thanks!

Correspondent bug: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/345627)

---

### Post by zevans on 2009-03-24
> **Nixie Pixel said:**
> I believe my pulse audio somehow broke completely a couple of days ago, likely due to a kernel update.  I now get only crackling noises, no sound at all, no matter what I do, or what I try to play.

I have seen notes regarding crackling above, but only with other sounds, not en lieu of them.  Does anyone know what having no sound at all, only crackling, might mean?

Thanks!
[PHP][/PHP]

I lost all sound after some updates late last week... turns out phonon-backend-xine had been replaced with phonon-backend-null - not something I would do on purpose so maybe some dependencies got in a tangle. Might be worth checking you still have a backend installed!

---

### Post by Nixie Pixel on 2009-03-24
> **taavikko said:**
> Correspondent bug: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/345627)
My symptoms are different. I have had no sound but crackling for days now. It doesn't matter if I restart any program or anything - restarting the computer greets me with crackling where there would be a login sound.  I have crackling when any sound is supposed to play, no matter what I do, until I shut down/restart again, and again I am greeted by crackling.

It may be the same bug, but the symptoms are different from those posted already.

---

### Post by danwood76 on 2009-03-24
You could install pavucontrol and see if any audio streams are active, if they are active kill them.
It could be that an app like an IM client or something is trying to play audio but pulse is messing it up so you get a constant stream of nonsense.

I've found that playing with the fragment size and count within the /etc/pulse/daemon.conf can give a varying performance increase with some apps but break others.
Although I am using the a52encode to give me digital surround output which is a hassle in itself with the latest pulse.

---

### Post by crimsun on 2009-03-24
> **Nixie Pixel said:**
> My symptoms are different. I have had no sound but crackling for days now. It doesn't matter if I restart any program or anything - restarting the computer greets me with crackling where there would be a login sound.  I have crackling when any sound is supposed to play, no matter what I do, until I shut down/restart again, and again I am greeted by crackling.

It may be the same bug, but the symptoms are different from those posted already.

A few things to check in this case:

1) distribution upgrades from Ubuntu 8.10 to 9.04 are problematic WRT ~/.gconf and ~/.pulse. You may wish to mv them out of the way from the command line (use ctrl+alt+F1 while *not* logged into GNOME);

2) as danwood suggested, install pavucontrol and check the default sink and configured sink(s) per stream. There are two known issues:
2a) certain ALSA mixer elements are muted on login (mostly affects Master, PCM, and Front);
2b) default sink has been migrated to RTP;

3) ensure that you're using my test kernels to work around bug 330814.

---

### Post by crimsun on 2009-03-24
As a note of clarification to my most recent post in this thread:

1) before you mv ~/.gconf and ~/.pulse, please ensure that pulseaudio is not running;

3) test kernel is at [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/) . Please check the SHA256SUMs of the downloaded debs before installing.

---

### Post by KhaaL on 2009-03-24
quick question crimsun, will you release a test kernel of 2.6.29?

---

### Post by vishalrao on 2009-03-24
You tried this? -> [http://drowninginbugs.blogspot.com/2009/03/call-for-testers-jaunty-64-bit.html](http://drowninginbugs.blogspot.com/2009/03/call-for-testers-jaunty-64-bit.html)

---

### Post by phenest on 2009-03-25
I normally use pcm to alter the volume, leaving both master and lfe on maximum. Pulse only shows the master volume.

---

### Post by novafluxx on 2009-03-26
Good to know these issues are being worked on! I'm getting intermittent static sometimes while I'm messaging in Pidgin. Sometimes, seemingly randomly, the sounds for outgoing messages [all that i've noticed] are replaced by a short burst of quiet static [hard to heard].

On a side note...everytime I boot up, my volume is at 0%! Whats up with this? Anyone know?

Keep up the amazing work!

---

### Post by andrewabc on 2009-03-26
> **novafluxx said:**
> 
On a side note...everytime I boot up, my volume is at 0%! Whats up with this? Anyone know?

It's a known bug.
[Strange volume control problem...](http://ubuntuforums.org/showthread.php?t=1101902)

---

### Post by morryis on 2009-03-26
Does flash-video playback in Firefox work for you? When I try to play a video in youtube, I hear that scratching sound and then the video stops, jumps a few frames, while audio is completely gone. When i close the tab, Firefox crashes.

Yesterday I did a fresh Jaunty install on a friends laptop and installed all Updates. Firefox and youtube are unusable, since it crashes on nearly every video with the same symptoms I described above.

---

### Post by andrewabc on 2009-03-26
> **morryis said:**
> Does flash-video playback in Firefox work for you? When I try to play a video in youtube, I hear that scratching sound and then the video stops, jumps a few frames, while audio is completely gone. When i close the tab, Firefox crashes.

Yesterday I did a fresh Jaunty install on a friends laptop and installed all Updates. Firefox and youtube are unusable, since it crashes on nearly every video with the same symptoms I described above.

Was compiz enabled? Maybe that caused problems.

---

### Post by eluminx on 2009-03-26
> **morryis said:**
> Does flash-video playback in Firefox work for you? When I try to play a video in youtube, I hear that scratching sound and then the video stops, jumps a few frames, while audio is completely gone. When i close the tab, Firefox crashes.

Yesterday I did a fresh Jaunty install on a friends laptop and installed all Updates. Firefox and youtube are unusable, since it crashes on nearly every video with the same symptoms I described above.

Video seems to work for me but audio is still a mystery.  I have tried both the 64 bit flash and the nonfree one from the repos.  Hopefully this is fixed by the time the RC drops.

---

### Post by ktp on 2009-03-26
> **morryis said:**
> Does flash-video playback in Firefox work for you? When I try to play a video in youtube, I hear that scratching sound and then the video stops, jumps a few frames, while audio is completely gone. When i close the tab, Firefox crashes.

Yesterday I did a fresh Jaunty install on a friends laptop and installed all Updates. Firefox and youtube are unusable, since it crashes on nearly every video with the same symptoms I described above.

Have been using the 64-bit flash and have not seen any issues.  Seems to work pretty good here.  I do see flash hangs once in blue moon but for alpha its great.

---

### Post by Diggs808 on 2009-03-28
> **morryis said:**
> Does flash-video playback in Firefox work for you? When I try to play a video in youtube, I hear that scratching sound and then the video stops, jumps a few frames, while audio is completely gone. When i close the tab, Firefox crashes.

Yesterday I did a fresh Jaunty install on a friends laptop and installed all Updates. Firefox and youtube are unusable, since it crashes on nearly every video with the same symptoms I described above.

I am having the same issue on flash videos.  Playback of a DVD using VLC works fine.  Anyone know if a bug has been filed on this already?  This would seem to be a show stopper.

---

### Post by biasquez on 2009-03-28
about crack/noise and errors with pulseaudio (like cpuoverload), maybe i solved problem setting this:

resample-method = speex-float-3

in /etc/pulse/daemon.conf

now i have two problem:
- [http://ubuntuforums.org/showthread.php?t=1101902](http://ubuntuforums.org/showthread.php?t=1101902)
- when i link my headphone, i hear sound from headphone and speakers
( i want to listen sound only from headphone)

---

### Post by danwood76 on 2009-03-28
The headphone thing is an alsa issue.
You used to press a switch in the old alsa volume control panel to make that work correctly.

---

### Post by biasquez on 2009-03-28
> **danwood76 said:**
> The headphone thing is an alsa issue.
You used to press a switch in the old alsa volume control panel to make that work correctly.

swith for headphone doesn't work but it depends on alsa, sorry for paste

---

### Post by chavanak on 2009-03-29
Had this problem initially but after upgrading to beta, the problem is gone. Sound plays perfectly and youtube is also working. Btw this is a laptop hp dv6602au. I had issues with my dsdt file and after solving it everything is working like a charm even the suspend/resume is now just perfect.
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

Just have a look in there, might solve your problem also :)

---

### Post by hanzomon4 on 2009-03-29
> **biasquez said:**
> swith for headphone doesn't work but it depends on alsa, sorry for paste

Did you find a fix? I got the same issue

---

### Post by hanzomon4 on 2009-03-29
Ah just fixed it.... In the volume control window there's a tab called switches. It only had one check box titled speaker. I unticked it and tada

---

### Post by Taiebot65 on 2009-04-01
I would like to report a bug really annoying with pulse audio or maybe is already existing and i would like to help to fix this bug...

So i have got a XFI xmod Usb sound card and my hda intel sound card..

If i plug my usb sound card with no sound stream when i start a stream pulse audio is unable to start...

But if i plug my usb sound card during a stream no problem the stream starts on my usb sound card...

Anyone?

1 17:28:04 home kernel: [  259.955398] usbcore: registered new interface driver hiddev
Apr  1 17:28:04 home kernel: [  260.007548] usbcore: registered new interface driver snd-usb-audio
Apr  1 17:28:04 home kernel: [  260.050184] input: Creative Technology Ltd Creative Xmod as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.3/input/input9
Apr  1 17:28:04 home kernel: [  260.092328] generic-usb 0003:041E:30D0.0001: input,hidraw0: USB HID v1.11 Device [Creative Technology Ltd Creative Xmod] on usb-0000:00:1d.0-2/input3
Apr  1 17:28:04 home kernel: [  260.092351] usbcore: registered new interface driver usbhid
Apr  1 17:28:04 home kernel: [  260.092355] usbhid: v2.6:USB HID core driver
Apr  1 17:28:05 home pulseaudio[3098]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

Apr  1 17:28:05 home pulseaudio[3098]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Apr  1 17:28:33 home pulseaudio[3098]: module-combine.c: Assertion '!op->outq_rtpoll_item_read && !op->inq_rtpoll_item_write' failed at modules/module-combine.c:691, function sink_process_msg(). Aborting.

---

### Post by Sockerdrickan on 2009-04-01
I have no sound at all running current 9.04
M-Audio revolution 7.1

---

### Post by stylishpants on 2009-04-02
> **Tux0r said:**
> I have no sound at all running current 9.04
M-Audio revolution 7.1

I also have the M-Audio Revolution 7.1, and sound works fine for me.

I clean-installed jaunty from the beta CD last night, and stereo sound worked immediately.
After updating to the latest packages this morning, still no problems.

All I had to do was edit /etc/pulse/daemon.conf and set the channels to 6 (and then turn up the volume in alsamixer) to get surround sound. Stereo output was already working.

---

### Post by Sockerdrickan on 2009-04-02
I guessed I managed to screw something up then, badly (new user doesn't help)

---

### Post by phenest on 2009-04-02
I get crackling from my laptop speakers if I mute the volume. I have an LFE channel, so LFE and Master are set to maximum, and PCM is used for volume control. If all 3 are muted, there is no crackling, but mute can only be applied to one of these using the mute keys on the keyboard.

Any ideas how to fix this?

---

### Post by amano on 2009-04-02
> **Tux0r said:**
> I guessed I managed to screw something up then, badly (new user doesn't help)

What about trying the Live CD?

---

### Post by Sockerdrickan on 2009-04-03
> **amano said:**
> What about trying the Live CD?
Either way I don't want to reinstall my system.

---

### Post by PiotrekS on 2009-04-07
I havent't sound too with my soundcard SB Audigy CA0106. 
System log:


> 
pulseaudio[3125]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.

pulseaudio[3125]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.

pulseaudio[3125]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

---

### Post by crimsun on 2009-04-07
> **Taiebot65 said:**
> I would like to report a bug really annoying with pulse audio or maybe is already existing and i would like to help to fix this bug...
Apr  1 17:28:33 home pulseaudio[3098]: module-combine.c: Assertion '!op->outq_rtpoll_item_read && !op->inq_rtpoll_item_write' failed at modules/module-combine.c:691, function sink_process_msg(). Aborting.

Please follow the proper procedure to file a bug. See the leading vertical edge (top) of this page.

---

### Post by crimsun on 2009-04-07
> **phenest said:**
> I get crackling from my laptop speakers if I mute the volume. I have an LFE channel, so LFE and Master are set to maximum, and PCM is used for volume control. If all 3 are muted, there is no crackling, but mute can only be applied to one of these using the mute keys on the keyboard.

Any ideas how to fix this?

Use the "default mixer tracks" section of the Sound preferences menu (Devices tab) to select which mixer elements are controlled by your hotkeys.

---

### Post by Taiebot65 on 2009-04-07
Hi crimsum i ve reported my bug 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/353683]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/353683")
... 
Hope you will find something...

---

### Post by phenest on 2009-04-07
> **crimsun said:**
> Use the "default mixer tracks" section of the Sound preferences menu (Devices tab) to select which mixer elements are controlled by your hotkeys.

I've done that, but the hotkeys only affect PCM, and muting only mutes PCM. How are you supposed to changes levels of different tracks easily, when the hotkeys only affect one track? It would be nice if muting muted all 3 tracks (Master, PCM, and LFE).

---

### Post by jocheem67 on 2009-04-08
Ha!!:p

It seems that the last daily updates of pulse repaired some annoying bugs:
I can use my volume-applet again and use  "preferences --- sound" again. This was broken on my AMD64 install. Very frustrating as I've been messing around to get it to work myself...
This bug was BTW already documented on launchpad.

Now I will give pulse a fair chance;)

---

### Post by gnomeuser on 2009-04-10
The following two patches from ALSA should make things a lot better for users of the Intel8x0 or Intel HDA cards:

[http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=fa00e046b41663cbda9b1affc0594669e5f14219](http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=fa00e046b41663cbda9b1affc0594669e5f14219)
[http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=bbf6ad1399e9516b0a95de3ad58ffbaed670e4cc](http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=bbf6ad1399e9516b0a95de3ad58ffbaed670e4cc)

Hopefully we will see them in Jaunty or in a test kernel soon.

---

### Post by crimsun on 2009-04-11
> **gnomeuser said:**
> The following two patches from ALSA should make things a lot better for users of the Intel8x0 or Intel HDA cards:

[http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=fa00e046b41663cbda9b1affc0594669e5f14219](http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=fa00e046b41663cbda9b1affc0594669e5f14219)
[http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=bbf6ad1399e9516b0a95de3ad58ffbaed670e4cc](http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=bbf6ad1399e9516b0a95de3ad58ffbaed670e4cc)

Hopefully we will see them in Jaunty or in a test kernel soon.

They're available (along with several other ALSA core fixes) at [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/) . These fixes bump the ABI and may need to be delayed until after Jaunty releases. Please comment on your experiences here in this thread and in bug 345627.

---

### Post by amano on 2009-04-11
crimsun, is there any ppa for those kernels?

Or are we supposed to install them manually with gdebi?

BTW, the direct link to the aforementioned bug is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

---

### Post by crimsun on 2009-04-11
> **amano said:**
> crimsun, is there any ppa for those kernels?

Or are we supposed to install them manually with gdebi?

BTW, the direct link to the aforementioned bug is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

There will not be a PPA (generated by me) containing those fixes, because those fixes have not been merged into our linux source yet. I understand that taking this approach generates a slightly higher bar for installing them and, thus, gaining testers. However, the ABI bump is a serious concern. I don't want people missing official kernel updates due to having installed my test kernel.

So: no, there is no PPA. Yes, you are supposed to install them manually. More than likely you will need linux-headers-2.6.28-12, linux-headers-2.6.28-12-generic, linux-libc-dev, linux-image-2.6.28-12-generic, linux-restricted-modules-common, and linux-restricted-modules-2.6.28-12-generic.

---

### Post by crimsun on 2009-04-12
Tim has indicated that the patches will be merged post-release in an SRU. I will be maintaining kernels as necessary in my [http://kernel.ubuntu.com/~dtchen](http://kernel.ubuntu.com/~dtchen) web space until they are released into -proposed.

---

### Post by crjackson on 2009-04-13
> **crimsun said:**
> Tim has indicated that the patches will be merged post-release in an SRU. I will be maintaining kernels as necessary in my [http://kernel.ubuntu.com/~dtchen](http://kernel.ubuntu.com/~dtchen) web space until they are released into -proposed.

Pardon my ignorance, but what is an SRU (service release unit perhaps)?

---

### Post by kansasnoob on 2009-04-13
> **crjackson said:**
> Pardon my ignorance, but what is an SRU (service release unit perhaps)?

Stable Release Update.

So it will come to you eventually thru the normal update cycle.

I like to begin every day with:

```
sudo apt-get update && sudo apt-get upgrade
```

During a development cycle I modify that:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by crjackson on 2009-04-13
> **kansasnoob said:**
> Stable Release Update.

So it will come to you eventually thru the normal update cycle.

I like to begin every day with:

```
sudo apt-get update && sudo apt-get upgrade
```

During a development cycle I modify that:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Ahhh... I see. Thanks for that kansasnoob.

---

### Post by forcecore on 2009-04-14
I repeat this here too that it should be fixed in final release because when i install Ubuntu 9.04 to someone i disable updates and someone has expensive mobile internet and cannot afford updates. When somethimg breaks because of updates then simple person has no skills to repair and they only need working system to read web news and use office or play media.

---

### Post by crimsun on 2009-04-14
> **forcecore said:**
> I repeat this here too that it should be fixed in final release

It will not be fixed in 9.04 final. Sorry, but the kernel is in deep freeze, and nothing short of a catastrophic failure that either corrupts filesystems or constitutes trivially exploitable remote privilege escalation will cause the kernel team and release manager to budge.

---

### Post by forcecore on 2009-04-14
looks like then best solution is killall -9 pulseaudio then.

---

### Post by amano on 2009-04-15
> **forcecore said:**
> looks like then best solution is killall -9 pulseaudio then.

That depends on the problem.

---

### Post by paradigm2 on 2009-04-16
> **crimsun said:**
> It will not be fixed in 9.04 final. Sorry, but the kernel is in deep freeze, and nothing short of a catastrophic failure that either corrupts filesystems or constitutes trivially exploitable remote privilege escalation will cause the kernel team and release manager to budge.

How long would you guesstimate until this reaches 9.04 via normal update channels?

If not within a few weeks, how may I best apply the kernel updates you host while minimizing future upgrade issues and/or conflicts?

I've already upgraded pulse audio to the new release via a PPA.  I'd probably like to go ahead and get the fixed kernel in there too.

Thank you.

---

### Post by kolslorr on 2009-04-17
Hi,

I have lost all sounds totally since upgrade to Jaunty Alpha, and I was hoping that the RC release will fix it, but sadly no.

I have done enough googling and read through all pages here, but to no avail. 

Will the final 9.04 fix all kinds of sound issues? I am rather lazy to look high and low for a fix myself....

---

### Post by paradigm2 on 2009-04-17
> **kolslorr said:**
> Hi,

I have lost all sounds totally since upgrade to Jaunty Alpha, and I was hoping that the RC release will fix it, but sadly no.

I have done enough googling and read through all pages here, but to no avail. 

Will the final 9.04 fix all kinds of sound issues? I am rather lazy to look high and low for a fix myself....

What kind of sound hardware have you?

```

lspci -v | grep audio
lspci -v | grep Audio

```

(Probably best to open your own thread for this rather than responding here)

---

### Post by sefs on 2009-04-17
Hi all I just installed the RC but my audio is scratchy or stuttery sometimes.  Is this me or is it a bug in pulse audio

---

### Post by kolslorr on 2009-04-17
> **paradigm2 said:**
> What kind of sound hardware have you?

```

lspci -v | grep audio
lspci -v | grep Audio

```

(Probably best to open your own thread for this rather than responding here)

Thanks. I have opened a thread here

[http://ubuntuforums.org/showthread.php?p=7092288#post7092288](http://ubuntuforums.org/showthread.php?p=7092288#post7092288)

---

### Post by crimsun on 2009-04-19
> **paradigm2 said:**
> How long would you guesstimate until this reaches 9.04 via normal update channels?

No idea.

> If not within a few weeks, how may I best apply the kernel updates you host while minimizing future upgrade issues and/or conflicts?

I normally track releases quite closely.

---

### Post by crimsun on 2009-04-19
> **sefs said:**
> Hi all I just installed the RC but my audio is scratchy or stuttery sometimes.  Is this me or is it a bug in pulse audio

Have you reproduced the symptom using my test kernel? (See earlier posts in this thread; you'll need the crimsun3 one.)

---

### Post by knavarathna92 on 2009-04-19
edit: problem solved

---

### Post by sefs on 2009-04-19
> **crimsun said:**
> Have you reproduced the symptom using my test kernel? (See earlier posts in this thread; you'll need the crimsun3 one.)

Can you elaborate on what these are...are they the kernels from the repos with a patch?

linux-source package deb seems to be missing.  Is there one?

I notice that all of them are not crimsun3 at the link provided...[http://kernel.ubuntu.com/~dtchen](http://kernel.ubuntu.com/~dtchen), but what about restriced modules and all that.

---

### Post by paradigm2 on 2009-04-19
> **sefs said:**
> Hi all I just installed the RC but my audio is scratchy or stuttery sometimes.  Is this me or is it a bug in pulse audio

Installing pulseaudio 9.0.15 along with the new alsa from the ppa referenced here:

[http://ubuntuforums.org/showpost.php?p=7092813&postcount=36](http://ubuntuforums.org/showpost.php?p=7092813&postcount=36)

As well as installing the new kernel 2.6.30rc2 from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/)

(Read this for help and warning on installing mainline kernels: [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds))

Solved all of my problems.  Sound (pulse) is very smooth now.

Crimson's test kernel mentioned already in this thread ( [http://kernel.ubuntu.com/~dtchen](http://kernel.ubuntu.com/~dtchen) ) is probably much SAFER and conservative though instead of installing 2.6.30.xx.  Some people report that 2.6.30 is messing things up for them, also you will be way out of synch with the official jaunty kernel.

My device:

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

---

### Post by mandelbr0t on 2009-04-19
Installed the Crimsun3 AMD64 kernel, and reinstalled PulseAudio from Jaunty repository. Exact same symptoms; Scratchy and stuttering sound under high CPU load, and occasionally the sound will deteriorate completely, causing constant stuttering. Only killing and restarting PulseAudio will fix it, and even then not for long. I've uninstalled PulseAudio again.

I am using this device for sound:
[FONT="Courier New"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)[/FONT]

And here's uname -a:
[FONT="Courier New"]Linux kosmo 2.6.28-12-generic #43~crimsun3lp345627 SMP Sat Apr 18 12:32:18 UTC 2009 x86_64 GNU/Linux[/FONT]

---

### Post by sefs on 2009-04-19
lol...I read that this will not be fixed in the release of jaunty next week earlier in the thread.  Is this actually true?  I have read how it was better integrated into jaunty than intrepid (in intrepid i had no problems I could recall).  Can it be disabled totally without removing it (pending fixing) in preference for alsa?

---

### Post by paradigm2 on 2009-04-19
> **mandelbr0t said:**
> Installed the Crimsun3 AMD64 kernel, and reinstalled PulseAudio from Jaunty repository. Exact same symptoms; Scratchy and stuttering sound under high CPU load, and occasionally the sound will deteriorate completely, causing constant stuttering. Only killing and restarting PulseAudio will fix it, and even then not for long. I've uninstalled PulseAudio again.

I am using this device for sound:
[FONT="Courier New"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)[/FONT]

And here's uname -a:
[FONT="Courier New"]Linux kosmo 2.6.28-12-generic #43~crimsun3lp345627 SMP Sat Apr 18 12:32:18 UTC 2009 x86_64 GNU/Linux[/FONT]


Crimsun will probably be around soon.

But did you install the new pulseaudio and alsa, etc from this special PPA:

[http://ubuntuforums.org/showpost.php?p=7092813&postcount=36](http://ubuntuforums.org/showpost.php?p=7092813&postcount=36)

If you just used the default Ubuntu repository, it is still on the old 9.0.14-xxx release.  An older alsa release as well.

I take back what I said earlier about it being perfect with the updates and the 2.6.30rc2 kernel and PA 9.0.15.  I did just experience a total sound loss and had to reboot.  But something else funky happened where I lost keyboard input as well so it isn't fair to blame the sound system for this.  When it works though, its working great unlike before.  Even the startup sound seems okay.   Before I was experiencing hard freezes upon startup when the startup sound was played approximately 30% of time.  :(

---

### Post by mandelbr0t on 2009-04-20
OK, so both upgrades are required. I've had no further sound issues since installing the Crimsun3 test kernel and PulseAudio 0.9.15 from the PPA.

---

### Post by biasquez on 2009-04-21
for me, with alsa 1.0.19 and pulseaudio 9.15 (without modded kernel) everything works fine!

---

### Post by sefs on 2009-04-21
> **biasquez said:**
> for me, with alsa 1.0.19 and pulseaudio 9.15 (without modded kernel) everything works fine!

Where did you get alsa 1.0.19 from?  Its not in the themuso repos.  I upgraded to pulse 9.15 and saw two libsound* at 1.0.19 but no alas that I could see.

---

### Post by biasquez on 2009-04-21
> **sefs said:**
> Where did you get alsa 1.0.19 from?  Its not in the themuso repos.  I upgraded to pulse 9.15 and saw two libsound* at 1.0.19 but no alas that I could see.

i'm using this script: [http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+hdmi](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+hdmi)

---

### Post by sefs on 2009-04-21
> **biasquez said:**
> i'm using this script: [http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+hdmi](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+hdmi)


Some quick questions

1) From that link "It'll reinstall kernel, kernel-headers and Alsa related packages".  Does this means it changes the default kernel in jaunty to a customized one of its own making? The kernel-headers as well?

2) I see 5 scripts listed...is it only the " AlsaUpgrade-1.0.x-rev-1.16.tar" I need?

Thanks.

---

### Post by sefs on 2009-04-21
Hey there is there anyway to easily go back to the default jaunty packages after using the themos repos?

The attached pic shows the packages that were installed/upgraded.

If i try to remove any of them it also list lots of other packages that will be removed.

I want to put back the jaunty default versions that came with jaunty.

Thanks.

---

### Post by ktp on 2009-04-21
> **sefs said:**
> Hey there is there anyway to easily go back to the default jaunty packages after using the themos repos?

The attached pic shows the packages that were installed/upgraded.

If i try to remove any of them it also list lots of other packages that will be removed.

I want to put back the jaunty default versions that came with jaunty.

Thanks.

I don't know if this is clean way to do it or not, but you can try installing the Jaunty packages using following:

```
sudo apt-get install <packageName>/jaunty <packageName>/jaunty ...
```

---

### Post by danwood76 on 2009-04-22
That wont work as the packages are built for jaunty so it wont do anything.

The way I did is was to remove all the packages and note down what else gets removed, it was only a coupld of extra packages.
Then once they are uninstalled disable the ppa and reinstall pulse and alsa and the extra apps.

---

### Post by sefs on 2009-04-22
> **danwood76 said:**
> That wont work as the packages are built for jaunty so it wont do anything.

The way I did is was to remove all the packages and note down what else gets removed, it was only a coupld of extra packages.
Then once they are uninstalled disable the ppa and reinstall pulse and alsa and the extra apps.

They were too many packages in my case ... but I think I found an easier way.  For me it was just 15 packages affected so I went thru the process below 15 times...

see what versions are in the apt cache
```

apt-cache showpkg <package-name>

```

The version numbers were listed at the very top and also at the very bottom of preceding command.

Then install the one with the version number I needed
```

sudo aptitude install <package-name>=<version-number>

```

---

