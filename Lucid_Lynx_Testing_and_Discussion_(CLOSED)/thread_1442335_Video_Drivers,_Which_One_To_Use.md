---
title: "Video Drivers, Which One To Use?"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-03-29
I'm a bit confused about video drivers. I'm testing Lucid Beta 1, and it is using  the nouveau driver I guess in place of Nvida? then there is fglrx? I'm using an iMac 24" LCD panel, my graphics card is the ATI Raedon HD 2400 series. Which video driver should I use? should I use the opensource ATI driver? and what is the difference between them? will one display graphics better than another? I'm not into 3D gaming, my primary concern is the way fonts are rendered in Linux. Will the video driver make a difference in font rendering?

Sorry for all the questions, but I am just confused as to which driver I should use.

Thanks,

Jaco

---

### Post by overdrank on 2010-03-29
Moved to Lucid Lynx Testing and Discussion

---

### Post by jaco223 on 2010-03-30
Bump

---

### Post by dino99 on 2010-03-30
go to synaptic

"nouveau" which is the generic open source video driver for nvidia card is not for your config.

Note that Lucid dont need by default a xorg.conf, so rename it by adding .old for example.

"fglrx" is for radeon & firegl ATI card, so try and see how it goes. (need fglrx-modaliases too)

If you want/need the latest/best packages: add   " ppa:xorg-edgers/ppa "  to synaptic repo ( system admin synaptic --> config repo third-apps +add), then update
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid)
might install xserver-xorg-video-ati

reboot

then go to system admin  hardware driver, you should have your drivers listed: activate one of them.

Resolution can be tweaked with system pref screen

---

### Post by ronacc on 2010-03-30
I'm nvidia so I can't help you with ATI but if you use the "search this forum" button in the lucid development forum you will find several threads on ATI drivers .

---

### Post by moviemaniac on 2010-03-30
I would jsut install Lucid which makes it use the opensource ATI drivers which - since they now support DRI2 and KMS and lots of other nice things - are generally preferrable. The ATI fglrx-driver lacks support for many modern features and since you don't play 3D games there's no need for you to install it. Font rendering has - at least to my knowledge - nothing to do with what kind of driver you're using. Leave it the way it is and all should be fine.

---

### Post by jaco223 on 2010-03-30
> **moviemaniac said:**
> I would jsut install Lucid which makes it use the opensource ATI drivers which - since they now support DRI2 and KMS and lots of other nice things - are generally preferrable. The ATI fglrx-driver lacks support for many modern features and since you don't play 3D games there's no need for you to install it. Font rendering has - at least to my knowledge - nothing to do with what kind of driver you're using. Leave it the way it is and all should be fine.

moviemaniac, so I just just install the ATI opensouce driver? how can i tell which driver the
kernel is loading? and do I need to blacklist any other video driver?

Thanks

Jaco

And thanks for the other replies as well.

---

### Post by moviemaniac on 2010-03-30
Jaco, if teh video card is already working the you are already using the opensource driver and you don't have to install anything ;)

---

### Post by Seren on 2010-03-30
> **jaco223 said:**
> moviemaniac, so I just just install the ATI opensouce driver?  how can i tell which driver the
kernel is loading? 


When you use the command 'lsmod' you see which modules were loaded by the kernel.

If I remember correctly, the open source driver should be named "radeon.ko" and the proprietary drivers should be named "fglrx.ko".

So if you see "radeon" somewhere in the list, you are already using the open source driver.

And as far as I remember the latest fglrx do not support card in the 2xxx range anymore. You need a r600, r700 or r800 chip, respectively correspond to 3xxx, 4xxx and 5xxx cards.


> 
and do I need to blacklist any other video driver?

Thanks

Jaco

And thanks for the other replies as well.

fgrlx package is not installed by default, so as long as you don't install it you'll be using the open source driver.

---

### Post by sdowney717 on 2010-03-30
No 3D then just use the radeon driver.
if 3D then use the ATI FGLRX driver

3D is not just for games. Google earth needs the 3D driver or it will run like molasses

---

### Post by jaco223 on 2010-03-30
> **dino99 said:**
> go to synaptic

"nouveau" which is the generic open source video driver for nvidia card is not for your config.

Note that Lucid dont need by default a xorg.conf, so rename it by adding .old for example.

"fglrx" is for radeon & firegl ATI card, so try and see how it goes. (need fglrx-modaliases too)

If you want/need the latest/best packages: add   " ppa:xorg-edgers/ppa "  to synaptic repo ( system admin synaptic --> config repo third-apps +add), then update
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid]("https://launchpad.net/%7Exorg-edgers/+archive/ppa?field.series_filter=lucid")
might install xserver-xorg-video-ati

reboot

then go to system admin  hardware driver, you should have your drivers listed: activate one of them.

Resolution can be tweaked with system pref screen

dino99, I am unable to add ppa.org-edgers/ppa to software sources, the option configure in synaptic is grayed out. I followed the link you provided and installed
xserver-xorg-video-ati, but nothing shows up in my hardware list.
Do other  packages need to be installed along with xserver-xorg-video-ati?

---

### Post by jaco223 on 2010-03-30
Seren, here is my lsmod. Assuming Radeon.

Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33357  4 
ppdev                    5259  0 
sco                        7853  2 
bridge                   45582  0 
stp                       1655  1 bridge
bnep                     9436  2 
l2cap                  30592  16 rfcomm,bnep
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203073  1 
snd_hda_intel          21781  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid_apple               4346  0 
radeon                673421  3 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
lib80211_crypt_tkip     7596  0 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
video                  17375  0 
usbhid                 36110  0 
hid                    66968  2 hid_apple,usbhid
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
applesmc               20069  0 
led_class               2864  1 applesmc
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
soundcore               6620  1 snd
wl                   1959694  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
output                  1871  1 video
drm                   162599  5 radeon,ttm,drm_kms_helper
intel_agp              24181  0 
i2c_algo_bit            5028  1 radeon
lp                      7028  0 
parport                32635  2 ppdev,lp
input_polldev           2482  1 applesmc
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
ohci1394               27174  0 
sky2                   40423  0 
ieee1394               81277  1 ohci1394
jaco@ubuntu:~$ 


Thanks for all the help guys.  Greatly appreciated!

---

### Post by sdowney717 on 2010-03-30
software sources is greyed out?
system-admin-software sources
are you gaining much if anything by using this ppa? over what your getting now with lucid?

---

### Post by jaco223 on 2010-03-30
> **sdowney717 said:**
> software sources is greyed out?
system-admin-software sources
are you gaining much if anything by using this ppa? over what your getting now with lucid?

sdowney, Software sources is not grayed out, just the configure option in synaptic. And I guess you're right I'm not really gaining much with the ppa. I suppose I should leave the ppa alone. Please forgive my lack of understanding, and knowledge. I'm still learning and trying to learn as much as I can. 

Thanks,

Jaco

---

### Post by Seren on 2010-03-30
My bad, contrary to what I said earlier, fglrx in Lucid is still supporting HD 2400 cards.(which use R600 chips).

---

### Post by dino99 on 2010-03-30
an other thread about your card

[http://ubuntuforums.org/showthread.php?p=9049163](http://ubuntuforums.org/showthread.php?p=9049163)

---

