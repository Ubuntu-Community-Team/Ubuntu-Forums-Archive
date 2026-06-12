---
title: "no sound after upgrade to 9.10"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by SurferGTO on 2009-11-16
a prior thread stated his problem was solved after updating his kernal, however mine is up to date and i still have no sound.

Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

---

### Post by delucamarco on 2009-11-21
Same here.

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)

---

### Post by dhavalbbhatt on 2009-11-21
Another user (don't mean to hijack this post, but would hate posting another with a similar problem) - no sound after fresh install of 9.10 64 bit.

Here is the relevant lspci -
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)

and here is the lsmod
```
Module                  Size  Used by
binfmt_misc            10220  1 
snd_hda_codec_nvhdmi     6048  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
iptable_filter          3872  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              10316904  36 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
i2c_nforce2             8168  0 
shpchp                 37756  0 
amd64_edac_mod         26688  0 
lp                     11908  0 
edac_core              48876  1 amd64_edac_mod
parport                40528  2 ppdev,lp
asus_atk0110            9472  0 
usbhid                 43968  0 
floppy                 65192  0 
video                  23612  0 
output                  3680  1 video
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
forcedeth              61292  0 

```

Any help will be greatly appreciated.

Thanks,
DB

---

### Post by SurferGTO on 2009-11-21
dhavalbbhatt and delucamarco what is your output of uname -a or uname -r.

this was solved in another post, ill get the link in a sec. it appears to be a kernel problem where during installation, if you chose to use the menu.lst currently active on your machine, 9.10 is installed however GRUB chooses to boot your prior kernel, causing conflict with the audio and possibley video card as well as other issues.

edit: [http://http://ubuntuforums.org/showthread.php?t=1307019&page=6]("http://http://ubuntuforums.org/showthread.php?t=1307019&page=6") is the page. solution on page 6. you should be working with the 14-generic solution and not the 15-generic, posted by user magnesium, tho it deepends on specifically which kernel you have.

---

### Post by oviorus on 2009-11-21
No audio for me either.

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

thank you.

---

### Post by oviorus on 2009-11-21
> **SurferGTO said:**
> dhavalbbhatt and delucamarco what is your output of uname -a or uname -r.

this was solved in another post, ill get the link in a sec. it appears to be a kernel problem where during installation, if you chose to use the menu.lst currently active on your machine, 9.10 is installed however GRUB chooses to boot your prior kernel, causing conflict with the audio and possibley video card as well as other issues.

edit: [http://http://ubuntuforums.org/showthread.php?t=1307019&page=6]("http://http://ubuntuforums.org/showthread.php?t=1307019&page=6") is the page. solution on page 6. you should be working with the 14-generic solution and not the 15-generic, posted by user magnesium, tho it deepends on specifically which kernel you have.
I'm sorry, you didn't ask me, but this is what I get by typing uname -r

2.6.31-14-generic

which as far as I understand is what I should get isn't?, however I can't hear any sound. Thank you.

---

### Post by LequidMetal on 2009-11-21
This may not help you but..
By default the volume on a fresh Karmic installation is set to 0 . Did you check the notification area for the volume level ?

---

### Post by SurferGTO on 2009-11-21
oviorus, there are still some other known issues with volume after a fresh install, like what liquid metal pointed out (volume being set to zero sometimes). tho mine was not like that. it has happend.

check out that other post i had a link to, it has a lot of other good suggestions and fixes, mine was just incase you were booting the older kernel.

---

### Post by oviorus on 2009-11-21
Thank you, my volume bar was at aroung 80%, I set it to 100% but can't hear anything yet, I'll be trying those other suggestions and fixes in your link, thank you.

Edit:
yay, installing linux-backports-modules-alsa-karmic-generic and rebooting did the trick.
Thank you!

---

### Post by SurferGTO on 2009-11-21
no worries, and good luck!

---

### Post by magnusvoug on 2009-11-21
> **SurferGTO said:**
> no worries, and good luck!
I also have no sound after upgrade to 9.10.My kernel is 2.6.28-16-generic
and have a hda indel sound card in a acer aspire 8930 laptop.
Befor upgrade sound was working nice.
I am new to linux but i am VERY HAPPY that i threw the vista out.
If someone can help it would be appriciated very much.
Thanks.

---

### Post by delucamarco on 2009-11-22
@ SurferGTO :

```
mdeluca@shuttle:~$ uname -a
Linux shuttle 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
```

EDIT: I followed the link you gave and it worked! It turned out that my audio card not working was just a symptom of the bigger problem deriving from the wrong kernel version being loaded. Thanks a bunch SurferGTO, once again a problem I thought I'd never fix was resolved thanks to the help of the community. Ubuntu rocks.

---

