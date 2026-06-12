---
title: "No sound in Ubuntu 10.4 LTS - Fresh Install - Dell Optiplex 380MT"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by erdanblo on 2010-05-05
Hi, i'm a Dell Optiplex 380 MT Workstation user which have a Intel HDA Integrated sound controller.

I was using Ubuntu 9.10 32 Bits Karmic, and all works fine, but, two days ago i did a fresh install to Ubuntu 10.4 LTS 32 Bits Lucid.

In Ubuntu 9.10 i didn't do nothing to make work all features of my workstation, but, in 10.4 LTS the sound don't work. The hardware appear in "Speaker Icon" and in the alsamixer menu, but nothing works. It's happens in the Live CD, Installation in Hard Disc, 32 Bits Version and 64 Bits version.

Here is the output of the command, in Ubuntu 9.10 & Ubuntu 10.4. The only difference that i see is the follow in lspci (bold text)

lspci

    Ubuntu 9.10: 00:1b.0 Audio device: Intel Corporation **82801G (ICH7 Family)** High Definition Audio Controller (rev 01)

    Ubuntu 10.4: 00:1b.0 Audio device: Intel Corporation **N10/ICH 7 Family** High Definition Audio Controller (rev 01)

At both version this is the which use (same output):
cat /proc/asound/card0/codec#0
Codec: Realtek ALC269


I've installed linux-backports-modules-alsa-2.6.32-21-generic-pae, reboot system and nothing happens.



lsmod | grep snd

Ubuntu 9.10.

    snd_hda_codec_realtek 203328 1
    snd_hda_intel 26920 4
    snd_hda_codec 75708 2 snd_hda_codec_realtek,snd_hda_intel
    snd_hwdep 7200 1 snd_hda_codec
    snd_pcm_oss 37920 0
    snd_mixer_oss 16028 1 snd_pcm_oss
    snd_pcm 75296 4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
    snd_seq_dummy 2656 0
    snd_seq_oss 28576 0
    snd_seq_midi 6464 0
    snd_rawmidi 22176 1 snd_seq_midi
    snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi
    snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
    snd_timer 22276 2 snd_pcm,snd_seq
    snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
    snd 59204 19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
    soundcore 7264 1 snd
    snd_page_alloc 9156 2 snd_hda_intel,snd_pcm

Ubuntu 10.4

    snd_hda_codec_realtek 208733 1
    snd_hda_intel 20384 4
    snd_hda_codec 79300 2 snd_hda_codec_realtek,snd_hda_intel
    snd_hwdep 5668 1 snd_hda_codec
    snd_pcm_oss 34571 0
    snd_mixer_oss 13961 1 snd_pcm_oss
    snd_pcm 71489 4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
    snd_seq_dummy 1498 0
    snd_seq_oss 27658 0
    snd_seq_midi 4621 0
    snd_rawmidi 19141 1 snd_seq_midi
    snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
    snd_seq 48170 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
    snd_timer 18720 2 snd_pcm,snd_seq
    snd_seq_device 6052 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
    snd 55971 21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se q_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_s eq,snd_timer,snd_seq_device
    soundcore 6620 1 snd
    snd_page_alloc 7236 2 snd_hda_intel,snd_pcm




Thank you for the help.

---

### Post by TBABill on 2010-05-05
Have you tried looking at the file /etc/modprobe.d/alsa-base.conf and seeing what the difference may be? You may need to edit the line near or at the end that starts with "option intel_hda_whatever" or something similar. If it works in 9.10 try to copy down what that line says in the file mentioned and then re-type it (as root) into alsa-base.conf in 10.04 (while placing # in front of the current line - don't delete that line so you can put it back like it was if needed), then save, restart and test out sound (headphones and speakers).

---

### Post by blackfox-bt on 2010-05-05
I have the same problem, but i don't have installed Ubuntu 10.4 LTS, i have upgraded my Ubuntu 9.10.

I don't know why, but Amarok works fine!, and the sound in login screen works too!.

If I try to play something in Totem or Rhythmbox, I cannot hear anything, only Amarok plays music.

**What can I do?**


> I am learning to speak in English, so I can make mistakes saying what i want. (I Speak Spanish)Testing:

I have opened the Rhythmbox after I have opened the PulseAudio (~$ pulseaudio & pavucontrol), I tried to play something in the Internet Radio (any station) and in the Output Devices from Volume Control I see that something was playing, but i cannot listen any thing, (Yes, I have the speakers connected and full of volume)

---

### Post by erdanblo on 2010-05-06
Well, i compared /etc/modprobe.d/alsa-base.conf the and the only the difference is in 9.10 conf appear this at the last line:

# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

I added this to my 10.4 alsa-base.conf and still don't work.


Any idea?


Thank you.


> **blackfox-bt said:**
> 
I don't know why, but Amarok works fine!, and the sound in login screen works too!.

Me don't play any sound. (No startup sound theme, no Firefox, no aplay test).

---

### Post by erdanblo on 2010-05-06
I founded that in Ubuntu 9.10 the codec detected is ALC259 and in Ubuntu 10.4 is detected as ALC269.

How i can change that?

---

### Post by erdanblo on 2010-05-06
Ok,

i'm trying with system beep with this C code:

[http://mark.koli.ch/2008/11/howto-make-your-linux-system-beep.html](http://mark.koli.ch/2008/11/howto-make-your-linux-system-beep.html)

I compiled the program, and test it.

Beep Works!, i can adjust volumen setting at alsamixer, and wheren it's a 0, beep don't make any sound, i adjust to more level, and the volumen of the sound grow (works fine).

I tested at both audio outputs, and both works. I think that output config is not the problem.

[IMG]http://i43.tinypic.com/s0x0xt.jpg[/IMG]

---

### Post by s_aldinger on 2010-05-06
I can confirm this behavior on the same model.... I have system beeps, but no music... very odd.

---

### Post by lidex on 2010-05-06
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by s_aldinger on 2010-05-06
[http://www.alsa-project.org/db/?f=8b58b9973e51240859afaee1bbb4c09fe1f096ae](http://www.alsa-project.org/db/?f=8b58b9973e51240859afaee1bbb4c09fe1f096ae)

---

### Post by morgoth85 on 2010-05-06
I have very similar problem. I cannot configure sound in system - preferences - sound. The only sound is from amarok (only 2 speakers from 5).
Also my gnome-volume-control-applet disappeared after upgrade to 10.4.
Weird

---

### Post by erdanblo on 2010-05-06
> **lidex said:**
> Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

****... this morning i used your script. I compared with my partner (he still use 9.10), and the only significant that i saw was the ALC259 when i use ALC269.

Tomorrow at works, i'll send you the url's, i can't see that now (i'm not at work).

---

### Post by lidex on 2010-05-06
Click the alsa-upgrade-script link in my sig and follow directions there to upgrade alsa. You seem to have a version mismatch. Report your results. But first update your system and then **reboot**:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by erdanblo on 2010-05-06
> **lidex said:**
> Click the alsa-upgrade-script link in my sig and follow directions there to upgrade alsa. You seem to have a version mismatch. Report your results. But first update your system and then **reboot**:
```
sudo apt-get update
sudo apt-get upgrade
```

My system is updated, i'm using the last kernel version which appear today (2.6.32-22, generic version).

I'll try alsa-update script, but 10.4 have a latest version of alsa of 9.10

I'll post results tomorrow in the morning.


By the way, did you read my previously post where i said that "system beep" works?


Thank you for your help.

---

### Post by lidex on 2010-05-06
> **erdanblo said:**
> My system is updated, i'm using the last kernel version which appear today (2.6.32-22, generic version).
I'll try alsa-update script, but 10.4 have a latest version of alsa of 9.10
I'll post results tomorrow in the morning.
By the way, did you read my previously post where i said that "system beep" works?
Thank you for your help.

And that is why people should start a new thread...I was looking at alsa-info for another poster. How about yours - you never posted it.

---

### Post by erdanblo on 2010-05-07
> **lidex said:**
> And that is why people should start a new thread...I was looking at alsa-info for another poster. How about yours - you never posted it.

Hi again!

I tried alsa update script, first -d, -c and the final, -i, reboot. And don't work.

Here is alsa-info:

Ubuntu 9.10: [http://www.alsa-project.org/db/?f=cfff93cd23568cca343a9b023db969381042fc8e](http://www.alsa-project.org/db/?f=cfff93cd23568cca343a9b023db969381042fc8e)
Ubuntu 10.4: [http://www.alsa-project.org/db/?f=845abfb13edc1e0ca6e0dd1d668ed0d27654b559](http://www.alsa-project.org/db/?f=845abfb13edc1e0ca6e0dd1d668ed0d27654b559)
Ubuntu 10.4 after Alsa-Update: [http://www.alsa-project.org/db/?f=2062705b6fc5c181b8ddad730f6262ab5c622c5f](http://www.alsa-project.org/db/?f=2062705b6fc5c181b8ddad730f6262ab5c622c5f)

---

### Post by TeRRaH on 2010-05-07
> **lidex said:**
> Right-click the alsa-info script link in my sig and "save as" to your user folder.
Your ALSA information is located at [http://www.alsa-project.org/db/?f=cbae8a2f9a1483cde52c4a040a50f2397d16dcba](http://www.alsa-project.org/db/?f=cbae8a2f9a1483cde52c4a040a50f2397d16dcba)

Sound is working in Amarok, but is not working at Firefox (video flash).

> !!Soundcards recognised by ALSA
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xcddf8000 irq 19

!!PCI Soundcards installed in the system
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


---

### Post by lidex on 2010-05-07
> **erdanblo said:**
> Hi again!

I tried alsa update script, first -d, -c and the final, -i, reboot. And don't work.

Here is alsa-info:

Ubuntu 9.10: [http://www.alsa-project.org/db/?f=cfff93cd23568cca343a9b023db969381042fc8e](http://www.alsa-project.org/db/?f=cfff93cd23568cca343a9b023db969381042fc8e)
Ubuntu 10.4: [http://www.alsa-project.org/db/?f=845abfb13edc1e0ca6e0dd1d668ed0d27654b559](http://www.alsa-project.org/db/?f=845abfb13edc1e0ca6e0dd1d668ed0d27654b559)
Ubuntu 10.4 after Alsa-Update: [http://www.alsa-project.org/db/?f=2062705b6fc5c181b8ddad730f6262ab5c622c5f](http://www.alsa-project.org/db/?f=2062705b6fc5c181b8ddad730f6262ab5c622c5f)

There are some issues with your codec, ALC259, which likely are solved with alsa 1.0.23. You can upgrade to that version using the same script but editing a few details via this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

Or try this fix:
[http://ubuntuforums.org/showpost.php?p=9241453&postcount=18]("http://ubuntuforums.org/showpost.php?p=9241453&postcount=18")

---

### Post by erdanblo on 2010-05-08
> **lidex said:**
> There are some issues with your codec, ALC259, which likely are solved with alsa 1.0.23. You can upgrade to that version using the same script but editing a few details via this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

Or try this fix:
[http://ubuntuforums.org/showpost.php?p=9241453&postcount=18]("http://ubuntuforums.org/showpost.php?p=9241453&postcount=18")

I don't know, but yesterday i did a fresh install of Ubuntu 10.4 but the sound card was identified by a ALC269, not 259 in Ubuntu 10.4 (Remenber, at 9.10 works, and it's identified by ALC269). But, it still don't work.

---

### Post by s_aldinger on 2010-05-11
> **lidex said:**
> There are some issues with your codec, ALC259, which likely are solved with alsa 1.0.23. You can upgrade to that version using the same script but editing a few details via this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2](http://ubuntuforums.org/showpost.php?p=9136618&postcount=2)

Or try this fix:
[http://ubuntuforums.org/showpost.php?p=9241453&postcount=18](http://ubuntuforums.org/showpost.php?p=9241453&postcount=18)


I've updated to 1.0.23 using your update script, to no effect.

new run of the info script can be found at [http://www.alsa-project.org/db/?f=580f4b9a96ef3f7a84cd3a34b617d375455f233d](http://www.alsa-project.org/db/?f=580f4b9a96ef3f7a84cd3a34b617d375455f233d)

---

### Post by lidex on 2010-05-11
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by chicco00 on 2010-05-12
hi to all, hi lidex.

i'm following this topic for a similar problem. Could i post here or i must open a new topic?
Sorry for this erdanblo. :)

edit:i lunched ur script on my desktop...could i attach it here?

---

### Post by yoonkit on 2010-05-12
Anybody got this working yet? 

I have done the alsa upgrade script and recompiled the latest version. I have checked that the recent patch [[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575793]](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575793]) is in /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/alsa-kernel/pci/hda/patch_realtek.c

But still it does not work. Im also on the Dell Optiplex 380

Thanks in advance.

yk

---

### Post by His Child on 2010-05-12
I have a similar problem.  web site audio did not work.  down loaded flash players etc. finally got it going.  then u tube did not work.  got that working after trial and error then rhythm box would not work. got that working.  but the next day no sound for anything.

When I had this trouble in ubuntu 9 I went to places   computer  - right  clicked on CD it brought up an option to share CD with all applications.  Up graded to 10.04 and have been struggling to get sound to work

went to the same process and finally remembered places computer rt click on CD to share  but now I get 
a error message

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I think sharing is the problem, but I don't know how to fis it

---

### Post by His Child on 2010-05-12
I just went to place computer  CD and picked option open with rhythmbox and now I have sound
everything works  web audio  Utube site [ [http://www.youtube.com/watch?v=lBxmDkhOXNE](http://www.youtube.com/watch?v=lBxmDkhOXNE) ] and rhythmbox

I don't understand it

I tried everything yesterday and spent the day in silence  :P

---

### Post by raygj on 2010-05-13
> **His Child said:**
> I just went to place computer  CD and picked option open with rhythmbox and now I have sound
everything works  web audio  Utube site [ [http://www.youtube.com/watch?v=lBxmDkhOXNE](http://www.youtube.com/watch?v=lBxmDkhOXNE) ] and rhythmbox

I don't understand it

I tried everything yesterday and spent the day in silence  :P

after upgrading alsa via script,[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")
 yesterday ,did you shut down the computer  then, yesterday, boot up to check sound ??

---

### Post by yoonkit on 2010-05-17
Without solving anything, I got sound working by rolling back my kernel version from 2.6.32 (lucid) to 2.6.31 (karmic) ... At least sounds work now.

---

### Post by jaezcurra on 2010-05-18
Tried everything and NO WAY.
Nobody knows how to fix something that was supposed to work with Karmic?
What did 2.6.32 break?   :confused:

---

### Post by jaezcurra on 2010-05-18
bump

---

### Post by mpaiva on 2010-05-18
Hi,
i m having the same problem.
We have 15 new Dell Optiplexs 380 at work with no sound on Ubuntu 10.04. :(

I ve tried everything without success.

---

### Post by jaezcurra on 2010-05-19
Same is happening to us at work: 5 computers with 10.04 with no sound and 6 ones with XP without problems   :(

---

### Post by thimindu on 2010-05-19
I've got the same problem.
It worked fine in 9.10. Hasn't worked since I upgraded to 10.04.

---

### Post by mpaiva on 2010-05-19
Ive opened this bug here. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199)


Whos having the same problem, please report there too.

---

### Post by imirciov on 2010-05-19
I have recently installed Ubuntu 10.04 Lucid on a new HP G62-144  DX, and initially I had no sound at all. Then, I found this link for upgrading ALSA, and the problem was mostly solved 
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
This enabled the system sound and sound with Flash player. Still, in order to have sound with the VLC player, I had to change the "audio output module" to "ALSA audio output".

---

### Post by baronoli on 2010-05-20
Same situation here, Dell Optiplex 380 with Integrated Sound Card RealTek ACL259 or ACL269 depending on Karmic or Lucid's interpretation. Sound was fine in KK but has gone in LL. 

Have tried every potential solution found on the net,
1. installing new Alsa drivers
2. modifying alsa-base.conf
3.rolling back Kernels

...all with no results. However I can get the speakers to beep using the system notifications. :) woo.

---

### Post by jaezcurra on 2010-05-20
> **mpaiva said:**
> Ive opened this bug here. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199)


Whos having the same problem, please report there too.

I did it this morning   :)

---

### Post by jaezcurra on 2010-05-24
May I encourage everyone facing this issue to go to the launchpad ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199)) and report it?

---

### Post by jaezcurra on 2010-05-28
It seems that a fix could make us see the light (hear a sound :)).  Go to [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199/comments/20](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199/comments/20) and try it.

---

### Post by Yehudah on 2010-05-31
> **jaezcurra said:**
> It seems that a fix could make us see the light (hear a sound :)).  

If not... it could make some of us go to a different distro.  I have not resolved this issue.  That, coupled with the ATI video issue and the restart/shutdown problem, make me want to dump Ubuntu for a different distribution.

---

### Post by en7777 on 2010-05-31
Hi.  I had the same problem.  Went to synaptic, and reinstalled the two flashplugin packages, and it works!

---

### Post by jaezcurra on 2010-06-01
> **jaezcurra said:**
> May I encourage everyone facing this issue to go to the launchpad ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/582199)) and report it?

THERE IS a fix.  Go to the Launchpad and check it   :)

---

