---
title: "Suspend to Ram and Hybernate Problems"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by a-user on 2010-04-12
Selecting Suspend to ram results in ubuntu preparing for the suspend mode, but it never powers down. it just freezes with a black screen and i hear my system vents louder than during normal phase.

if i use reset button or i power down via power button the system even refuses to go into post (bios). i have to cut down power source.


hybernate seems to work a bit better. it still cannot power down the pc. but if i power down it manually it at least restart after i power it on again. but like in ubuntu 9.10 it does not resume imediatly afterwards, it first runs through all post messages of the bios. and when it comes to linux resuming from hybernate this works partially. it resumes, but several services report failing (like alsa, lirc...).

on my ubuntu 9.10 suspend works perfect, while hybernate at least pwoers down but in rest it has similar problems.

hence both are worse than in karmic, suspend even totaly broken.

i'm not sure what informations i should provide and i wonder if it hapens also to others.

---

### Post by wilee-nilee on 2010-04-12
Is the swap at least equal to your ram amount? gparted is where you can look.

---

### Post by a-user on 2010-04-12
ofocurse. i have a swap partion that is about 10GB, while my ram is 4GB. but in case of suspend to ram it shouldn't matter anyway.

so, shall i understand from your post that for you it's working good?

---

### Post by wilee-nilee on 2010-04-12
> **a-user said:**
> ofocurse. i have a swap partion that is about 10GB, while my ram is 4GB. but in case of suspend to ram it shouldn't matter anyway.

so, shall i understand from your post that for you it's working good?

No problems here, That is probably way more swap then you need, usually a equal to ram is fine. Suspend moves ram to swap so it is important, your computer would not suspend or hibernate with less then a equal ram to swap.

I suspect the problem is with the computer, some just don't work without a little tweaking. Unfortunately I have no clue as how to fix this though.

---

### Post by a-user on 2010-04-12
on the same computer with a same sized swap partion but on ubuntu karmic suspend works perfect, and hybernate as describved above.

hence i dont think it's related to the computer.

---

### Post by a-user on 2010-04-12
no one else with this issue? no other infos?

---

### Post by TheNessus on 2010-04-12
Happens to me too since yesterday's update. Never happened before. Always worked 100% on Karmic and Jaunty... so no, it's not a computer issue.

Do you have Nvidia like I do?

---

### Post by a-user on 2010-04-12
what do you mean by that? did it worked with lucid beta 1?
i started using lucid with the beta 2 prerelease on thurstday. and at this time it already didn't worked. and it still doesn't.

yes i have an nvidia card.

i read on the inet, that there is a suspend.log file. i will look into it when i come home. maybe i get tehre some information what causes this issue.

but beside of that, regarding hybernation. using it on windows, it avoids post messages and directly starts to resume when i press power. i mean, it does not run through the first bios boot stuff.

using ubuntu (since karmic) i allways must go through bios post messages beofore it starts resuming from disk. is it only me? or is this normal behaviour? it makes hybernation totally useless even if i wouldn't had the issues that some services are broken after resume. rebooting is even on karmic faster.

---

### Post by a-user on 2010-04-12
Well, now at home i made a suspend (not hybernate). and i am here posting now the pm-suspend.log. i cannot discover any issues in it. all seems fine. but still the computer does not power down. and pressing power button does not resume, neither with a keyboard button. pressing reset button reboots (although not allways).

edit: i just want to repeat. on same machine karmic performs the suspend (not hybernate) perfectly. i can dual boot into carmic here.

it is as if acpi functions of luvid are broken. well here the log:

> Initial commandline parameters: 
Mon Apr 12 20:48:08 CEST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux htpc 2.6.32-20-generic #29-Ubuntu SMP Fri Apr 9 20:35:00 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
snd_hda_codec_nvhdmi    14218  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
isl6421                 1781  1 
snd_hda_intel          23768  0 
snd_hda_codec          99451  2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               6938  1 snd_hda_codec
snd_pcm_oss            40569  0 
snd_mixer_oss          16442  1 snd_pcm_oss
snd_pcm                88141  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1878  0 
snd_seq_oss            31586  0 
cx24116                16533  1 
cx88_dvb               22321  6 
cx88_vp3054_i2c         2207  1 cx88_dvb
videobuf_dvb            6139  1 cx88_dvb
dvb_core              102929  2 cx88_dvb,videobuf_dvb
snd_seq_midi            5733  0 
snd_rawmidi            23161  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57588  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23087  2 snd_pcm,snd_seq
snd_seq_device          7080  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71943  14 snd_hda_codec_nvhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
tuner                  23224  0 
bitblit                 5811  1 fbcon
snd_page_alloc          8724  2 snd_hda_intel,snd_pcm
softcursor              1565  1 bitblit
nvidia              10799466  28 
vga16fb                12757  1 
cx8800                 32410  0 
cx8802                 14861  1 cx88_dvb
cx88xx                 80093  3 cx88_dvb,cx8800,cx8802
ir_common              43415  1 cx88xx
i2c_algo_bit            6024  2 cx88_vp3054_i2c,cx88xx
tveeprom               13882  1 cx88xx
v4l2_common            18357  3 tuner,cx8800,cx88xx
videodev               40486  4 tuner,cx8800,cx88xx,v4l2_common
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    12020  1 videodev
videobuf_dma_sg        12370  4 cx88_dvb,cx8800,cx8802,cx88xx
lp                      9336  0 
parport                37160  2 ppdev,lp
lirc_imon              26413  1 
lirc_dev               11302  3 lirc_imon
btcx_risc               4384  3 cx8800,cx8802,cx88xx
vgastate                9857  1 vga16fb
videobuf_core          19269  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
i2c_piix4               9639  0 
joydev                 11072  0 
k10temp                 2308  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
psmouse                64608  0 
serio_raw               4918  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
usb_storage            49833  0 
ohci1394               30548  0 
pata_atiixp             4209  0 
r8169                  39970  0 
mii                     5237  1 r8169
ahci                   37646  3 
ieee1394               94798  1 ohci1394
             total       used       free     shared    buffers     cached
Mem:       4056952    2721796    1335156          0     123600    1752836
-/+ buffers/cache:     845360    3211592
Swap:     10000452          0   10000452
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Apr 12 20:48:10 CEST 2010: performing suspend

---

### Post by a-user on 2010-04-13
edit: removed.

maybe someone else sees something usefull in the log

---

### Post by Darkav on 2010-04-13
I have the same behaviour, but the suspend works (only) from the login page after a reboot...

---

### Post by meborc on 2010-04-13
i have heard that when you use **nouveau** driver, you have stand by and hibernation and when you use the **proprietary** driver you loose them

check which driver you use, try switching them and report back

---

### Post by a-user on 2010-04-13
indeed i'm using the proprietary driver. i will test if it works with nouveau. but i find it strange that the log file claims all working fine. the pc simply does not power of although video and all other things stoped properly.

i report back later, when i'm back home and have tested this.

---

### Post by a-user on 2010-04-13
tested it with the nouveau driver: same thing happens. still does not work, still no failor in the log.

well, i also opened a bug report in launchpad.... wonder how they broke it in lucid :(

---

### Post by a-user on 2010-04-22
well, nothing changed. i hope they fix this till final release or i'm forced to stay with karmic.

---

### Post by Miguel on 2010-04-22
For a few months (december 2009?) suspend works OK the first time on my T400. The second time I try it, it will go to sleep but never wake up. I don't know if it's a kernel issue, a BIOS issue or what. 

Even more unfortunately, I remember when all was working perfectly, and it was so nice... I'm starting to suspect it's a BIOS thingie that lenovo changed, though. I'll have to test it with a fresh install of ubunu 8.10 (where suspend worked perfectly) or 9.04. Let's see...

---

### Post by a-user on 2010-04-26
i tested calling pm-suspend directly: same problem. it finishes all for suspend, an no problems so far. but when it comes to the moment it should power off the system (well, most of it as it is suspend to ram) i only hear one of my fans louder and screen is black.

that's it. only reset button or holding power off button for 4 sec works.

i really hope this works in final. i updated daily but still no solution so far.

p.s. currently i found far more peaople with the very same or similar issue.

---

### Post by Darkav on 2010-04-29
> **a-user said:**
> (..)

p.s. currently i found far more peaople with the very same or similar issue.

I am one of them...any news about this problem?

---

