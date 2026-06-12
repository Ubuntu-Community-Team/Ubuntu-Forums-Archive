---
title: "No sound anymore (but volume app works!)"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by djst on 2010-03-12
Background: I was a little adventurous (again) and upgraded to 10.4 alpha, and things are working quite well. The main reason why I upgraded was because I had occasional wireless network problems on 9.10, and it's a bit better in 10.4 (less frequent disconnects that force me to reboot). 

My problem: after upgrading, I have no audio. The volume applet seems to be working, and no errors are reported... it's just that it's always completely silent. Any idea why?

I'm on a ThinkPad T400s and the system test identifies my sound card as:

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2620000 irq 17

---

### Post by autumnraine on 2010-03-12
Same problem here. Suddenly there's no sound in any program or system activity, whereas there was before.

---

### Post by lidex on 2010-03-13
Check your levels in:
```
alsamixer
```

Make sure you're using correct kernel
```
sudo update-grub
```
[Reboot needed]

---

### Post by nhasian on 2010-03-13
I just upgraded today as well and after the upgrade, no sound!  I was easily able to fix it by going to System->Preferences->Sound then the Output Tab, change the Connector drop down box from Analog Output to Analog Speakers.  that fixed it for me.

> **djst said:**
> My problem: after upgrading, I have no audio. The volume applet seems to be working, and no errors are reported... it's just that it's always completely silent. Any idea why?


---

### Post by cleentrax on 2010-03-13
my sound stopped working today and i have nothing in sound preferences output except for dummy. i have standard onboard intel sound chip.

---

### Post by kansasnoob on 2010-03-13
I just did a fresh install today and I also have a sound issue. Every time I reboot I end up with no sound. The volume widget in Indicator Applet even looks odd, like instead of **[COLOR="Red"]<)))[/COLOR]** just **[COLOR="Red"]<--[/COLOR]**.

If I try to fix things by left clicking the volume applet everything I try to adjust also adjusts everything else. However I always install "gnome-alsamixer" which is just a front end to alsamixer that shows up in Sound & Video, so if I readjust things there I easily get my sound back for the entire session.

---

### Post by lidex on 2010-03-13
> **kansasnoob said:**
> I just did a fresh install today and I also have a sound issue. Every time I reboot I end up with no sound. The volume widget in Indicator Applet even looks odd, like instead of **[COLOR="Red"]<)))[/COLOR]** just **[COLOR="Red"]<--[/COLOR]**.

If I try to fix things by left clicking the volume applet everything I try to adjust also adjusts everything else. However I always install "gnome-alsamixer" which is just a front end to alsamixer that shows up in Sound & Video, so if I readjust things there I easily get my sound back for the entire session.

You could try adding this to your startup as a workaround:
```
bash -c "sleep 15 ; amixer set Master playback unmute"
```
Are the sliders down also or just muted?

---

### Post by lidex on 2010-03-13
> **cleentrax said:**
> my sound stopped working today and i have nothing in sound preferences output except for dummy. i have standard onboard intel sound chip.

Can you post output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by lidex on 2010-03-13
> **djst said:**
> Background: I was a little adventurous (again) and upgraded to 10.4 alpha, and things are working quite well. The main reason why I upgraded was because I had occasional wireless network problems on 9.10, and it's a bit better in 10.4 (less frequent disconnects that force me to reboot). 

My problem: after upgrading, I have no audio. The volume applet seems to be working, and no errors are reported... it's just that it's always completely silent. Any idea why?

I'm on a ThinkPad T400s and the system test identifies my sound card as:

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2620000 irq 17

Have you checked for muted elements in alsamixer?

---

### Post by dcstar on 2010-03-14
> **cleentrax said:**
> my sound stopped working today and i have nothing in sound preferences output except for dummy. i have standard onboard intel sound chip.

Mine stopped too, on boot-up my volume icon shows muted.

It seems an update has broken things.

---

### Post by mattlach on 2010-03-14
My sound suddenly stopped working as well.

After having it functioning well ever since I installed 9.10 today I suddenly have no sound.

When I go to the volume slider to check the configuration it says that the sound is going to a "dummy stereo output".  Under the hardare tab there are no options listed.

I'm guessing something upgraded recently and as such my system is no longer detecting and loading modules for my sound hardware.

I don't know what may have changed lately.

It's frustrating when stuff like this happens, as I don't have time to research the potetial impact of every upgrade before I upgrade it...

---

### Post by mattlach on 2010-03-14
> **mattlach said:**
> My sound suddenly stopped working as well.

After having it functioning well ever since I installed 9.10 today I suddenly have no sound.

When I go to the volume slider to check the configuration it says that the sound is going to a "dummy stereo output".  Under the hardare tab there are no options listed.

I'm guessing something upgraded recently and as such my system is no longer detecting and loading modules for my sound hardware.

I don't know what may have changed lately.

It's frustrating when stuff like this happens, as I don't have time to research the potetial impact of every upgrade before I upgrade it...

Never mind.

A reboot fixed mine.  I must have updated something Alsa or kernel related, forgotten about it, and forgotten to reboot.

---

### Post by Saghaulor on 2010-03-15
I don't have sound. I just installed Lucid Alpha3, amd64, and I have nothing.

```
aplay -l
```
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
lspci | grep Audio
```
> 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

Please help.

---

### Post by lidex on 2010-03-15
> **Saghaulor said:**
> I don't have sound. I just installed Lucid Alpha3, amd64, and I have nothing.

```
aplay -l
```


```
lspci | grep Audio
```


Please help.

Have you read the thread and checked everything mentioned?

---

### Post by Saghaulor on 2010-03-15
> **lidex said:**
> Have you read the thread and checked everything mentioned?

Yeah I read it.

First thing that I checked was volume levels. 

Oddly enough, I get sound from the headphone jack, but not from the speakers.

---

### Post by lidex on 2010-03-15
> **Saghaulor said:**
> Yeah I read it.

First thing that I checked was volume levels. 

Oddly enough, I get sound from the headphone jack, but not from the speakers.

Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Saghaulor on 2010-03-15
> **lidex said:**
> Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Thank you. Please see attached.

---

### Post by bsutt on 2010-03-15
Just in case this catches anyone else:

My experience was that the new sound applet picked the incorrect audio device.  Rather than my onboard sound chip it selected the HDMI audio device served up by my graphics card.

To change, click the audio applet, sound preferences, output tab and double check the correct device is checked.  Sound has been fine since.

---

### Post by lidex on 2010-03-15
First thing to try is installing alsa-backports. You'll need to make sure backports repo is enabled. "Applications>System>Administration>Software Sources" On the "Updates" tab make sure the top four boxes are checked. Close that out.
In a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

Reboot. Check levels in alsamixer. Make sure that "thing" in the panel is unmuted as well.

---

### Post by Saghaulor on 2010-03-15
> **lidex said:**
> Reboot. Check levels in alsamixer. Make sure that "thing" in the panel is unmuted as well.

'that "thing"', haha.

Will try. Thanks for the heads up.

---

### Post by Saghaulor on 2010-03-15
Well, that didn't seem to help. See the attached screenshot that shows my volume levels and that the package is installed.

---

### Post by lidex on 2010-03-15
Gotcha. In alsamixer screenie you have right-pointing carets which means there are more mixer elements there. You can scroll to them using arrow keys. What I think is more to the point is the soundcard showing there "Intel G45 DEVIBX". Press F6 to select another entry - I'm thinking "Realtek ALC272"

Edit:
Open for editing your alsa-base.conf file:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the end:
```
options snd-hda-intel model=gateway
``` 
Save file, close and reboot.

---

### Post by Saghaulor on 2010-03-15
> **lidex said:**
> Gotcha. In alsamixer screenie you have right-pointing carets which means there are more mixer elements there. You can scroll to them using arrow keys. What I think is more to the point is the soundcard showing there "Intel G45 DEVIBX". Press F6 to select another entry - I'm thinking "Realtek ALC272"

It seems that "Intel G45" is all that's available.

---

### Post by lidex on 2010-03-15
I edited my previous post, have a look.

---

### Post by Saghaulor on 2010-03-15
> **lidex said:**
> I edited my previous post, have a look.
Ill try in the morning. Thanks for all your help.

---

### Post by Saghaulor on 2010-03-16
No luck. See attached.

Also, I found the following interesting bit from /usr/share/doc/alsa-base/driver/HD-Audio.txt

> Speaker and Headphone Output
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
One of the most frequent (and obvious) bugs with HD-audio is the
silent output from either or both of a built-in speaker and a
headphone jack.  In general, you should try a headphone output at
first.  A speaker output often requires more additional controls like
the external amplifier bits.  Thus a headphone output has a slightly
better chance.

Before making a bug report, double-check whether the mixer is set up
correctly.  The recent version of snd-hda-intel driver provides mostly
"Master" volume control as well as "Front" volume (where Front
indicates the front-channels).  In addition, there can be individual
"Headphone" and "Speaker" controls.

Ditto for the speaker output.  There can be "External Amplifier"
switch on some codecs.  Turn on this if present.

Another related problem is the automatic mute of speaker output by
headphone plugging.  This feature is implemented in most cases, but
not on every preset model or codec-support code.

In anyway, try a different model option if you have such a problem.
Some other models may match better and give you more matching
functionality.  If none of the available models works, send a bug
report.  See the bug report section for details.

If you are masochistic enough to debug the driver problem, note the
following:

- The speaker (and the headphone, too) output often requires the
  external amplifier.  This can be set usually via EAPD verb or a
  certain GPIO.  If the codec pin supports EAPD, you have a better
  chance via SET_EAPD_BTL verb (0x70c).  On others, GPIO pin (mostly
  it's either GPIO0 or GPIO1) may turn on/off EAPD.
- Some Realtek codecs require special vendor-specific coefficients to
  turn on the amplifier.  See patch_realtek.c.
- IDT codecs may have extra power-enable/disable controls on each
  analog pin.  See patch_sigmatel.c.
- Very rare but some devices don't accept the pin-detection verb until
  triggered.  Issuing GET_PIN_SENSE verb (0xf09) may result in the
  codec-communication stall.  Some examples are found in
  patch_realtek.c.


However, it's not very promising with statements like "If you are masochistic enough to debug the driver problem. . " So I'm going to try to learn more about patch_realtek.c as I don't believe it's masochistic to expect the speaker to work.

---

### Post by dash86no on 2010-03-16
I have the same problem: I can get sound from headphones but nothing from the speakers. 

Please see my system info below:

[http://www.alsa-project.org/db/?f=86810b271a84ee74d50a70d620d671ac676ef8a8](http://www.alsa-project.org/db/?f=86810b271a84ee74d50a70d620d671ac676ef8a8)

Thanks,

DA

---

### Post by Saghaulor on 2010-03-16
From what I gather patch_realtek.c is already integrated into the kernel.

[https://lists.ubuntu.com/archives/kernel-team/2006-May/000867.html]("https://lists.ubuntu.com/archives/kernel-team/2006-May/000867.html")

This might be helpful.
[http://osdir.com/ml/linux-kernel/2009-02/msg04563.html]("http://osdir.com/ml/linux-kernel/2009-02/msg04563.html")

> ALC272 needs EAPD for speaker outputs as well as other similar ALC
codecs.

I feel like I'm getting somewhere, but I don't really know much about this stuff.

---

### Post by Saghaulor on 2010-03-16
This seems to be helpful.
[https://bugzilla.redhat.com/show_bug.cgi?id=509542]("https://bugzilla.redhat.com/show_bug.cgi?id=509542")

Specifically this thread.
[https://bugzilla.redhat.com/show_bug.cgi?id=509542#c7]("https://bugzilla.redhat.com/show_bug.cgi?id=509542#c7")

This seems to be the answer, although I don't know how to use hda_analyzer.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/393523/comments/14]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/393523/comments/14")

---

### Post by Saghaulor on 2010-03-16
I don't know what to do. Any help would be appreciated.

From the above posts it looks like I need to have EAPD enabled. Please help.

---

### Post by Saghaulor on 2010-03-16
Here's the hda_analyzer.

[http://www.alsa-project.org/main/index.php/HDA_Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")

---

### Post by Saghaulor on 2010-03-16
The problem: 

My internal speakers were not producing sound, however, the headphone jack was. HDA-Intel seemed to be the culprit.

The solution:

Download hda_analyzer from [http://www.alsa-project.org/main/index.php/HDA_Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")
Enabled EAPD (for me it was Node 0x15), and viola, internal speakers are producing sound.

---

### Post by Saghaulor on 2010-03-16
However, the EAPD switch is not saved at shutdown, so I must enable it at ever start up.

Please assist with a permanent fix.

---

### Post by lidex on 2010-03-16
Wow. That's impressive detective work, good job. I was going blind at 3 AM reading the documentation. I'll see if I can help you with that last bit although I have a sneaking suspicion you'll get there first. I think I lurnt sumthin ;)

---

### Post by Saghaulor on 2010-03-16
> **lidex said:**
> Wow. That's impressive detective work, good job. I was going blind at 3 AM reading the documentation. I'll see if I can help you with that last bit although I have a sneaking suspicion you'll get there first. I think I lurnt sumthin ;)

Thanks. I try to give back what I can.

I think I have to modify the codec, to enable EAPD, but I don't know how to do that.

I tracked down some modules that ended in .ko, I wasn't able to open them. I wonder if I'm going to have to compile ALSA. IDK.

Worst case I guess is that I'll have to do the hda_analyzer every time I boot and want sound.

Interesting thing, my computer has crashed repeatedly while playing around with this stuff. I have a feeling it might be from Rhythmbox because I believe it's open every time the system hangs. Not sure yet, will try to narrow down the variables.

Btw, should I file a bug with this EAPD thing? I'm not sure where to file it at if filing a bug is what I should be doing.

---

### Post by lidex on 2010-03-16
Do any of these match what you have:
```

  3stack-dig	    3-stack (2-channel) with SPDIF
  3stack-6ch	    3-stack (6-channel)
  3stack-6ch-dig     3-stack (6-channel) with SPDIF
  6stack-dig	    6-stack with SPDIF
```
A stack represents an audio jack

---

### Post by lidex on 2010-03-16
I noted your Alsa driver is v 1.0.21
1.0.22.1 is available and I have a hunch that upgrading that and installing alsa-firmware along with adding the correct line (from above post) to alsa-base.conf could do the trick. The link to alsa upgrade script is in my sig.

---

### Post by Saghaulor on 2010-03-16
> **lidex said:**
> Do any of these match what you have:
```

  3stack-dig	    3-stack (2-channel) with SPDIF
  3stack-6ch	    3-stack (6-channel)
  3stack-6ch-dig     3-stack (6-channel) with SPDIF
  6stack-dig	    6-stack with SPDIF
```
A stack represents an audio jack

I don't know if those apply. I know that I have SPDIF, and I have HDMI as well, so I'm not sure if the HDMI has 6ch, also, I don't know what the stack is.

Does your script backup the files that it modifies? I'm worried about something not working properly and then what working things I have will not work.

---

### Post by lidex on 2010-03-16
There is a restore option. Follow the link for documentation. Not my script, BTW, it's soundcheck's thread!

Do you have 3 or 6 audio jacks?

Before you update the driver install alsa-tools and alsa-firmware from medibuntu repository and make sure you are running latest kernel.

---

### Post by lidex on 2010-03-16
> **Saghaulor said:**
> Thanks. I try to give back what I can.

I think I have to modify the codec, to enable EAPD, but I don't know how to do that.

I tracked down some modules that ended in .ko, I wasn't able to open them. I wonder if I'm going to have to compile ALSA. IDK.

Worst case I guess is that I'll have to do the hda_analyzer every time I boot and want sound.

Interesting thing, my computer has crashed repeatedly while playing around with this stuff. I have a feeling it might be from Rhythmbox because I believe it's open every time the system hangs. Not sure yet, will try to narrow down the variables.

Btw, should I file a bug with this EAPD thing? I'm not sure where to file it at if filing a bug is what I should be doing.

This being an alpha release, I think the crashing/freezing is non-related. There are a number of threads regarding this. Interestingly mentioned more than once was that RhythmBox continued to play despite the system freeze.

EAPD with ALC272 is a known issue apparently and has been addressed in newer alsa releases:
>     - ALSA: hda - Add missing initialization for ALC272 
    ALC272 needs EAPD for speaker outputs as well as other similar ALC 
    codecs. 

---

### Post by Saghaulor on 2010-03-16
Btw,

Not to get off topic, but the crashing wasn't from Rhythmbox, I didn't even have it open this time. I wonder if the EAPD switch is causing it. I looked through the logs right around the time that it happened and there's nothing informative.

Weird.

I'll keep my eye peeled when I don't have EAPD on to verify that it's not causing the problem.

---

### Post by Saghaulor on 2010-03-16
> **lidex said:**
> This being an alpha release, I think the crashing/freezing is non-related. There are a number of threads regarding this. Interestingly mentioned more than once was that RhythmBox continued to play despite the system freeze.

EAPD with ALC272 is a known issue apparently and has been addressed in newer alsa releases:

Check you out. That helps a lot.

Actually, I had that happen once. The system hung with Rhythmbox still playing.

---

### Post by djst on 2010-03-17
Wow, lots of replies in here!

After some research, I can also confirm that my headphone jack works fine, so the problem is limited to the internal speakers.

I tried to download and run HDAAnalyzer but I can't find an entry for EAPD?

I checked alsamixer and all levels are at the max (100). The only levels i see are Master and PCM.

aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: HDA Generic [HDA Generic]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by Saghaulor on 2010-03-17
> **djst said:**
> Wow, lots of replies in here!

After some research, I can also confirm that my headphone jack works fine, so the problem is limited to the internal speakers.

I tried to download and run HDAAnalyzer but I can't find an entry for EAPD?

I checked alsamixer and all levels are at the max (100). The only levels i see are Master and PCM.

aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: HDA Generic [HDA Generic]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I had to dig around for a minute to find the EAPD switch. I'll include a screen shot so you sort of know what you're looking for.

Although you have a different chipset, so we may not have the same problem.

---

### Post by djst on 2010-03-17
> **Saghaulor said:**
> I had to dig around for a minute to find the EAPD switch. I'll include a screen shot so you sort of know what you're looking for.

Although you have a different chipset, so we may not have the same problem.

Thanks for all your help. I found it now (can't believe I didn't go through all options!), but nothing changes when enabling it. 

I've also fiddled around with a lot of other settings (taking care to revert afterward to not mess things up), but nothing seems to make the speaker actually vibrate.

---

### Post by Saghaulor on 2010-03-18
Sorry djst,
I'm not really sure how to help you. Best of luck. Hopefully they'll get this work out for you and me by the final release.

---

### Post by djst on 2010-03-18
> **Saghaulor said:**
> Sorry djst,
I'm not really sure how to help you. Best of luck. Hopefully they'll get this work out for you and me by the final release.

Yeah, and thanks for your nice attempts.

Worst case I'll just reinstall from scratch, and until then, I'll use headphones when I need audio. :)

---

### Post by Saghaulor on 2010-03-18
djst,

Did you try the Alsa upgrade script? I haven't tried it yet, but lidex suggested I try it. Perhaps that would resolve your problem too.[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alc272]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alc272")

---

### Post by tekstr1der on 2010-03-18
Ouch... Got my Lenovo ThinkPad X201s today and have been bitten by this bug. Oddly, I had sound for at least a few reboots at gdm, logon sound, and window/button sounds. It was only after I disabled those that I can get no more sound whatsoever.

```
:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
```
:~$ apt-cache policy alsa-base
alsa-base:
  Installed: 1.0.22.1+dfsg-0ubuntu3
  Candidate: 1.0.22.1+dfsg-0ubuntu3
  Version table:
 *** 1.0.22.1+dfsg-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by lidex on 2010-03-18
> **tekstr1der said:**
> Ouch... Got my Lenovo ThinkPad X201s today and have been bitten by this bug. Oddly, I had sound for at least a few reboots at gdm, logon sound, and window/button sounds. It was only after I disabled those that I can get no more sound whatsoever.

```
:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
```
:~$ apt-cache policy alsa-base
alsa-base:
  Installed: 1.0.22.1+dfsg-0ubuntu3
  Candidate: 1.0.22.1+dfsg-0ubuntu3
  Version table:
 *** 1.0.22.1+dfsg-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status

```

You should run the alsa-info script so we can get the full picture. Right-click the link in my sig and "save as" to your user folder. then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```

Post a link to the script output in your next post.

---

### Post by Saghaulor on 2010-03-22
lidex,

I tried the Alsa upgrade script, my Alsa is now up to date, but I still don't have any audio from my speakers without enabling EAPD through hda_analyzer tool.

---

### Post by lidex on 2010-03-22
OK, now it's time to figure out what line(s) to add to alsa-base.conf
It is a two step process.

---

### Post by Saghaulor on 2010-03-23
> **lidex said:**
> OK, now it's time to figure out what line(s) to add to alsa-base.conf
It is a two step process.

Okay, can you fill me in on these steps?

I'm not sure what or how to modify what must be modified. I don't seen anything in the alsa-base.conf that resembles the pin settings that are offered in the alsa-info script.

The script lists the pin settings under HDA-Intel Codec information, but when I search for HDA-Intel, I only find HDA-Intel.conf, which doesn't seem to be what I need.

---

### Post by lidex on 2010-03-23
You've already done step one, which is updating alsa, at least I think so. Run this command to see your installed version:
```
cat /proc/asound/version
```

Step two is inserting the proper lines in alsa-base.conf so alsa knows how to configure properly. I posted about that previously and also that EAPD has been fixed in alsa. You should probably look for a bios update as well.

---

### Post by Saghaulor on 2010-03-24
> **lidex said:**
> You've already done step one, which is updating alsa, at least I think so. Run this command to see your installed version:
```
cat /proc/asound/version
```

Step two is inserting the proper lines in alsa-base.conf so alsa knows how to configure properly. I posted about that previously and also that EAPD has been fixed in alsa. You should probably look for a bios update as well.

Thanks for the baby steps lidex.

Below is verification that I compiled Alsa.> stephenaghaulor@stephenaghaulor-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar  8 2010 for kernel 2.6.32-16-generic (SMP).
stephenaghaulor@stephenaghaulor-laptop:~$

If by "inserting the proper lines in alsa-base.conf" you mean, options snd-hda-intel model=gateway, then that line was added previously.
> stephenaghaulor@stephenaghaulor-laptop:~$ cat /etc/modprobe.d/alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
#Added in attempt to debug speaker issue
options snd-hda-intel model=gateway
stephenaghaulor@stephenaghaulor-laptop:~$

I'm not sure how this is a BIOS issue, as the speakers work as expected in Windows.

Perhaps the EAPD setting is not fixed?

Once again, thanks for your help.

---

### Post by Saghaulor on 2010-03-24
lidex,

Sorry about the last post. 

I reread your post regarding changing alsa-base.conf, and I added 3stack-dig to alsa-base, and what do you know, I have speakers working at boot.

Thanks for all your help friend.

I've certainly learned a lot from this experience.

---

### Post by Swagman on 2010-03-24
I'm testing Lucid 64 out on a USB stick and am having the same "no Sound - Dummy Output" issue.

No sound with headphones either.

9:10 i386 sound works a treat.

---

### Post by Saghaulor on 2010-03-24
> **Swagman said:**
> I'm testing Lucid 64 out on a USB stick and am having the same "no Sound - Dummy Output" issue.

No sound with headphones either.

9:10 i386 sound works a treat.

We're going to need more info if you would like us to help you.

Please run the alsa info script and post your results.[Alsa Info Script]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")

---

### Post by Swagman on 2010-03-25
> **Saghaulor said:**
> We're going to need more info if you would like us to help you.

Please run the alsa info script and post your results.[Alsa Info Script]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")

Not really looking for a fix as it's only a test on a USB stick (That's now full), just chipping in with a " I got this issue as well".

I'm pretty sure it'll be sussed by release time.

---

### Post by lidex on 2010-03-25
> **Saghaulor said:**
> lidex,

Sorry about the last post. 

I reread your post regarding changing alsa-base.conf, and I added 3stack-dig to alsa-base, and what do you know, I have speakers working at boot.

Thanks for all your help friend.

I've certainly learned a lot from this experience.

You're welcome. Knew it had to be there somewhere ;)
Enjoy.

---

### Post by lidex on 2010-03-25
> **Swagman said:**
> Not really looking for a fix as it's only a test on a USB stick (That's now full), just chipping in with a " I got this issue as well".

I'm pretty sure it'll be sussed by release time.

Cross your fingers!

---

### Post by mcwho on 2010-04-01
I have a similar issue where the headphone jack works but the built in speakers do not. I just got this [Gateway NV7915u]("http://www.bestbuy.com/site/Gateway+-+Laptop+with+Intel%26%23174;+Core%26%23153;+i3+Processor+-+NightSky+Black/9695393.p?skuId=9695393&ci_src=14110944&ci_sku=9695393&ref=06&loc=01&id=1218150610770") laptop and really love it as it is a great value for the performance and stays very cool.

[Here]("http://www.alsa-project.org/db/?f=61f236f72fa0e4bf3465b8b9b7ca9af7bc9c059a") is the output from the Alsa script.

I did not upgrade Alsa instead just tried adding the following options to my /etc/modprobe.d/alsa-base.conf file:

[INDENT]3stack-dig	    3-stack (2-channel) with SPDIF
3stack-6ch	    3-stack (6-channel)[/INDENT]

The last line reads:

[INDENT]options snd-hda-intel model=3stack-dig power_save=10 power_save_controller=N[/INDENT]

Both work in a sense meaning sound comes from the built in speakers now but no longer works with the headphone jack. I have played with the 'Sound Preferences' and levels in the 'Gnome Alsa Mixer'. Using 'Analog Stereo Duplex' selected from the 'Hardware' tab in 'Sound Preferences'. This leaves me with two 'Connector:' choices in the 'Output' tab in 'Sound Preferences'. 'Analog Headphones' and 'Analog Output' respectively. The results are as follows:

[INDENT]3stack-dig: Analog Headphones=sound from speakers only, Analog Output=sound from speakers only a little louder though

3stack-6ch-dig: Analog Headphones=no sound, Analog Output=sound from speakers only[/INDENT]

Also from the [specs]("http://www.gateway.com/systems/product/529668369.php") for my laptop:

[INDENT]headphone/Speaker/Line-Out Jack with S/PDIF support[/INDENT]

Being that I am using Alsa 1.0.21 but had to upgrade to kernel 2.6.33-020633-generic to get the [Arrandale Intel Graphics]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10") to work and the sound works from either the headphone jack or the internal speakers but not both I am led to believe the fix is finding the right option to put into alsa-base.conf.

Anyone have any ideas? Does the fix you found allow you to select which source you would like sound from? Also if you insert headphones while audio is playing from the internal speakers does it mute the speakers and play only through the headphones?

---

### Post by mcwho on 2010-04-01
Sorry. I just looked at the placement of this thread. I am running 9.10 but had to upgrade the kernel to get the Arrandale Graphics working. I am not running Lucid as this thread relates. However I felt like I should note my experiences somewhere to help anyone who may stumble on this solution. Meaning hopefully they will try just adding the line to alsa-base.conf as a first line of attack...

---

### Post by lidex on 2010-04-01
> **mcwho said:**
> Sorry. I just looked at the placement of this thread. I am running 9.10 but had to upgrade the kernel to get the Arrandale Graphics working. I am not running Lucid as this thread relates. However I felt like I should note my experiences somewhere to help anyone who may stumble on this solution. Meaning hopefully they will try just adding the line to alsa-base.conf as a first line of attack...

snd-hda-intel options for gateway:
```
Gateway model=gateway
gt5405e model=gateway
T-1616 model=dell-m42
mx (not all) model=m2-2
nx (not all) model=m6
P-6831FX, 6860-fx
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
```

snd-hda-intel options for ALC272:
```
ALC662/663/272
==============
  3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)

```

See this page:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

3-stack may not be your configuration. How many audio jacks do you have and how many sound channels? 

Also I recommend upgrading alsa (see link in my sig). My laptop required both the upgrade and adding options to work in Jaunty.

---

### Post by Saghaulor on 2010-04-06
> **mcwho said:**
> I have a similar issue where the headphone jack works but the built in speakers do not. I just got this [Gateway NV7915u]("http://www.bestbuy.com/site/Gateway+-+Laptop+with+Intel%26%23174;+Core%26%23153;+i3+Processor+-+NightSky+Black/9695393.p?skuId=9695393&ci_src=14110944&ci_sku=9695393&ref=06&loc=01&id=1218150610770") laptop and really love it as it is a great value for the performance and stays very cool.

[Here]("http://www.alsa-project.org/db/?f=61f236f72fa0e4bf3465b8b9b7ca9af7bc9c059a") is the output from the Alsa script.

I did not upgrade Alsa instead just tried adding the following options to my /etc/modprobe.d/alsa-base.conf file:

[INDENT]3stack-dig	    3-stack (2-channel) with SPDIF
3stack-6ch	    3-stack (6-channel)[/INDENT]

The last line reads:

[INDENT]options snd-hda-intel model=3stack-dig power_save=10 power_save_controller=N[/INDENT]

Both work in a sense meaning sound comes from the built in speakers now but no longer works with the headphone jack. I have played with the 'Sound Preferences' and levels in the 'Gnome Alsa Mixer'. Using 'Analog Stereo Duplex' selected from the 'Hardware' tab in 'Sound Preferences'. This leaves me with two 'Connector:' choices in the 'Output' tab in 'Sound Preferences'. 'Analog Headphones' and 'Analog Output' respectively. The results are as follows:

[INDENT]3stack-dig: Analog Headphones=sound from speakers only, Analog Output=sound from speakers only a little louder though

3stack-6ch-dig: Analog Headphones=no sound, Analog Output=sound from speakers only[/INDENT]

Also from the [specs]("http://www.gateway.com/systems/product/529668369.php") for my laptop:

[INDENT]headphone/Speaker/Line-Out Jack with S/PDIF support[/INDENT]

Being that I am using Alsa 1.0.21 but had to upgrade to kernel 2.6.33-020633-generic to get the [Arrandale Intel Graphics]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10") to work and the sound works from either the headphone jack or the internal speakers but not both I am led to believe the fix is finding the right option to put into alsa-base.conf.

Anyone have any ideas? Does the fix you found allow you to select which source you would like sound from? Also if you insert headphones while audio is playing from the internal speakers does it mute the speakers and play only through the headphones?

Shoot, I just realized that my headphone jack isn't working now either.

---

### Post by Saghaulor on 2010-04-06
Interesting thing.

Remember this?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150248&d=1268701277[/IMG]

Well look at it now. Please see attached.

The headphones are disabled. Weird.

---

### Post by lidex on 2010-04-06
> **mcwho said:**
> I have a similar issue where the headphone jack works but the built in speakers do not. [Here]("http://www.alsa-project.org/db/?f=61f236f72fa0e4bf3465b8b9b7ca9af7bc9c059a") is the output from the Alsa script.
[ headphones?

 Remove the power entries from alsa-base.conf and then
upgrade alsa - the link is in my sig.

---

### Post by PizzAp on 2010-04-21
Anyone else suddenly got sound upon:
```
sudo udevadm trigger --action=add --subsystem-match=sound     
```

Mixer and PulseAudio Volume Meters work fine before.

---

