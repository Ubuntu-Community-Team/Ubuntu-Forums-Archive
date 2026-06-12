---
title: "System errors"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by zhenia on 2015-09-05
Hi,
I keep getting system error message after update installations; and some things I cannot install at all.
For example some videos do not get streamed any more, I get the message that a plug in must be installed but when I try I get a
Package dependencies cannot be resolved
message

 The following packages have unmet dependencies:

gstreamer1.0-libav: Depends: libavcodec-extra-54 (>= 6:9.13) but 6:9.18-0ubuntu0.14.04.1 is to be installed
                    Depends: libavformat54 (>= 6:9.1-1) but 6:9.18-0ubuntu0.14.04.1 is to be installed
                    Depends: libavutil52 (>= 6:9.1-1) but 6:9.18-0ubuntu0.14.04.1 is to be installed
                    Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.6 is to be installed
                    Depends: libglib2.0-0 (>= 2.37.3) but 2.40.2-0ubuntu1 is to be installed
any help possible?

And these system error popups after each update are annoying!

Thanks!

---

### Post by zhenia on 2015-09-05
here is what i found in var/crash folder
```
ProblemType: Package
DKMSBuildLog:
 DKMS make.log for alsa-hda-0.1.1somerville for kernel 3.13.0-63-generic (x86_64)
 Sat Sep  5 17:17:23 CEST 2015
 make -C /lib/modules/3.13.0-63-generic/build M=/var/lib/dkms/alsa-hda/0.1.1somerville/build modules
 make[1]: Entering directory `/usr/src/linux-headers-3.13.0-63-generic'
   CC [M]  /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.o
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:48:8: error: redeclaration of enumerator &#8216;SND_PR_ALWAYS&#8217;
         SND_PR_ALWAYS,
         ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:28:0:
 include/sound/core.h:336:2: note: previous definition of &#8216;SND_PR_ALWAYS&#8217; was here
   SND_PR_ALWAYS,
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:49:8: error: redeclaration of enumerator &#8216;SND_PR_DEBUG&#8217;
         SND_PR_DEBUG,
         ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:28:0:
 include/sound/core.h:337:2: note: previous definition of &#8216;SND_PR_DEBUG&#8217; was here
   SND_PR_DEBUG,
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:50:8: error: redeclaration of enumerator &#8216;SND_PR_VERBOSE&#8217;
         SND_PR_VERBOSE,
         ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:28:0:
 include/sound/core.h:338:2: note: previous definition of &#8216;SND_PR_VERBOSE&#8217; was here
   SND_PR_VERBOSE,
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:676:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_UNKNOWN&#8217;
   SNDRV_CHMAP_UNKNOWN = 0,
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:468:2: note: previous definition of &#8216;SNDRV_CHMAP_UNKNOWN&#8217; was here
   SNDRV_CHMAP_UNKNOWN = 0,
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:677:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_NA&#8217;
   SNDRV_CHMAP_NA,  /* N/A, silent */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:469:2: note: previous definition of &#8216;SNDRV_CHMAP_NA&#8217; was here
   SNDRV_CHMAP_NA,  /* N/A, silent */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:678:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_MONO&#8217;
   SNDRV_CHMAP_MONO, /* mono stream */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:470:2: note: previous definition of &#8216;SNDRV_CHMAP_MONO&#8217; was here
   SNDRV_CHMAP_MONO, /* mono stream */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:680:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FL&#8217;
   SNDRV_CHMAP_FL,  /* front left */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:472:2: note: previous definition of &#8216;SNDRV_CHMAP_FL&#8217; was here
   SNDRV_CHMAP_FL,  /* front left */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:681:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FR&#8217;
   SNDRV_CHMAP_FR,  /* front right */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:473:2: note: previous definition of &#8216;SNDRV_CHMAP_FR&#8217; was here
   SNDRV_CHMAP_FR,  /* front right */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:682:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_RL&#8217;
   SNDRV_CHMAP_RL,  /* rear left */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:474:2: note: previous definition of &#8216;SNDRV_CHMAP_RL&#8217; was here
   SNDRV_CHMAP_RL,  /* rear left */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:683:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_RR&#8217;
   SNDRV_CHMAP_RR,  /* rear right */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:475:2: note: previous definition of &#8216;SNDRV_CHMAP_RR&#8217; was here
   SNDRV_CHMAP_RR,  /* rear right */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:684:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FC&#8217;
   SNDRV_CHMAP_FC,  /* front center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:476:2: note: previous definition of &#8216;SNDRV_CHMAP_FC&#8217; was here
   SNDRV_CHMAP_FC,  /* front center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:685:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_LFE&#8217;
   SNDRV_CHMAP_LFE, /* LFE */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:477:2: note: previous definition of &#8216;SNDRV_CHMAP_LFE&#8217; was here
   SNDRV_CHMAP_LFE, /* LFE */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:686:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_SL&#8217;
   SNDRV_CHMAP_SL,  /* side left */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:478:2: note: previous definition of &#8216;SNDRV_CHMAP_SL&#8217; was here
   SNDRV_CHMAP_SL,  /* side left */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:687:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_SR&#8217;
   SNDRV_CHMAP_SR,  /* side right */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:479:2: note: previous definition of &#8216;SNDRV_CHMAP_SR&#8217; was here
   SNDRV_CHMAP_SR,  /* side right */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:688:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_RC&#8217;
   SNDRV_CHMAP_RC,  /* rear center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:480:2: note: previous definition of &#8216;SNDRV_CHMAP_RC&#8217; was here
   SNDRV_CHMAP_RC,  /* rear center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:690:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FLC&#8217;
   SNDRV_CHMAP_FLC, /* front left center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:482:2: note: previous definition of &#8216;SNDRV_CHMAP_FLC&#8217; was here
   SNDRV_CHMAP_FLC, /* front left center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:691:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FRC&#8217;
   SNDRV_CHMAP_FRC, /* front right center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:483:2: note: previous definition of &#8216;SNDRV_CHMAP_FRC&#8217; was here
   SNDRV_CHMAP_FRC, /* front right center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:692:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_RLC&#8217;
   SNDRV_CHMAP_RLC, /* rear left center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:484:2: note: previous definition of &#8216;SNDRV_CHMAP_RLC&#8217; was here
   SNDRV_CHMAP_RLC, /* rear left center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:693:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_RRC&#8217;
   SNDRV_CHMAP_RRC, /* rear right center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:485:2: note: previous definition of &#8216;SNDRV_CHMAP_RRC&#8217; was here
   SNDRV_CHMAP_RRC, /* rear right center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:694:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FLW&#8217;
   SNDRV_CHMAP_FLW, /* front left wide */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:486:2: note: previous definition of &#8216;SNDRV_CHMAP_FLW&#8217; was here
   SNDRV_CHMAP_FLW, /* front left wide */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:695:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FRW&#8217;
   SNDRV_CHMAP_FRW, /* front right wide */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:487:2: note: previous definition of &#8216;SNDRV_CHMAP_FRW&#8217; was here
   SNDRV_CHMAP_FRW, /* front right wide */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:696:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FLH&#8217;
   SNDRV_CHMAP_FLH, /* front left high */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:488:2: note: previous definition of &#8216;SNDRV_CHMAP_FLH&#8217; was here
   SNDRV_CHMAP_FLH, /* front left high */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:697:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FCH&#8217;
   SNDRV_CHMAP_FCH, /* front center high */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:489:2: note: previous definition of &#8216;SNDRV_CHMAP_FCH&#8217; was here
   SNDRV_CHMAP_FCH, /* front center high */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:698:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_FRH&#8217;
   SNDRV_CHMAP_FRH, /* front right high */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:490:2: note: previous definition of &#8216;SNDRV_CHMAP_FRH&#8217; was here
   SNDRV_CHMAP_FRH, /* front right high */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:699:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TC&#8217;
   SNDRV_CHMAP_TC,  /* top center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:491:2: note: previous definition of &#8216;SNDRV_CHMAP_TC&#8217; was here
   SNDRV_CHMAP_TC,  /* top center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:700:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TFL&#8217;
   SNDRV_CHMAP_TFL, /* top front left */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:492:2: note: previous definition of &#8216;SNDRV_CHMAP_TFL&#8217; was here
   SNDRV_CHMAP_TFL, /* top front left */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:701:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TFR&#8217;
   SNDRV_CHMAP_TFR, /* top front right */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:493:2: note: previous definition of &#8216;SNDRV_CHMAP_TFR&#8217; was here
   SNDRV_CHMAP_TFR, /* top front right */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:702:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TFC&#8217;
   SNDRV_CHMAP_TFC, /* top front center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:494:2: note: previous definition of &#8216;SNDRV_CHMAP_TFC&#8217; was here
   SNDRV_CHMAP_TFC, /* top front center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:703:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TRL&#8217;
   SNDRV_CHMAP_TRL, /* top rear left */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:495:2: note: previous definition of &#8216;SNDRV_CHMAP_TRL&#8217; was here
   SNDRV_CHMAP_TRL, /* top rear left */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:704:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TRR&#8217;
   SNDRV_CHMAP_TRR, /* top rear right */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:496:2: note: previous definition of &#8216;SNDRV_CHMAP_TRR&#8217; was here
   SNDRV_CHMAP_TRR, /* top rear right */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:705:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_TRC&#8217;
   SNDRV_CHMAP_TRC, /* top rear center */
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:497:2: note: previous definition of &#8216;SNDRV_CHMAP_TRC&#8217; was here
   SNDRV_CHMAP_TRC, /* top rear center */
   ^
 In file included from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:30:0:
 /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_local.h:706:2: error: redeclaration of enumerator &#8216;SNDRV_CHMAP_LAST&#8217;
   SNDRV_CHMAP_LAST = SNDRV_CHMAP_TRC,
   ^
 In file included from include/sound/asound.h:39:0,
                  from include/sound/control.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:25,
                  from /var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.c:29:
 include/uapi/sound/asound.h:508:2: note: previous definition of &#8216;SNDRV_CHMAP_LAST&#8217; was here
   SNDRV_CHMAP_LAST = SNDRV_CHMAP_BRC,
   ^
 make[2]: *** [/var/lib/dkms/alsa-hda/0.1.1somerville/build/patch_analog.o] Error 1
 make[1]: *** [_module_/var/lib/dkms/alsa-hda/0.1.1somerville/build] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-63-generic'
 make: *** [all] Error 2
DKMSKernelVersion: 3.13.0-63-generic
Date: Sat Sep  5 17:17:26 2015
DuplicateSignature: dkms:alsa-hda-dkms:0.1.1somerville:/var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:48:8: error: redeclaration of enumerator &#8216;SND_PR_ALWAYS&#8217;
Package: alsa-hda-dkms 0.1.1somerville
PackageVersion: 0.1.1somerville
SourcePackage: dkms-hda
Title: alsa-hda-dkms 0.1.1somerville: alsa-hda kernel module failed to build

```

---

### Post by tgalati4 on 2015-09-05
Open a terminal:

```
sudo apt-get -f install
```

Cut and paste the output.  Use quote or code tags.  Don't say yes to the repairs just yet.  Do you have an PPA's installed?

---

### Post by zhenia on 2015-09-06
i had tried apt-get install yesterday before posting here so it is relatively clean ;)

sudo output 
```

The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-62 linux-headers-3.13.0-62-generic
  linux-image-3.13.0-62-generic linux-image-extra-3.13.0-62-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


```

sorry what is a PPA?

---

### Post by tgalati4 on 2015-09-06
PPA is a personal package archive--something that is added when you install software from someplace else (other than Ubuntu's main software repositories.)

Post the output of your repositories:

```
cat /etc/apt/sources.list
```

and 

```
cat /etc/apt/sources.list.d/official-package-repositories.list
```

Take note of any other repositories in that directory:

```
ls -la /etc/apt/sources.list.d
```

All it takes is one bad repository to mess up your system.

Also, clean up unneeded files:

```
sudo apt-get autoremove
```

Then clean and check:

```
sudo apt-get clean
sudo apt-get check
```

---

### Post by zhenia on 2015-09-06
```

cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://archive.ubuntu.com/ubuntu/ trusty universe
deb http://archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main



deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

```

```

cat /etc/apt/sources.list.d/official-package-repositories.list
cat: /etc/apt/sources.list.d/official-package-repositories.list: No such file or directory


```

```

ls -la /etc/apt/sources.list.d
total 24
drwxr-xr-x 2 root root 4096 May 29 11:33 .
drwxr-xr-x 6 root root 4096 May 26 22:40 ..
-rw-r--r-- 1 root root  176 May 29 11:33 google-chrome.list
-rw-r--r-- 1 root root  176 May 26 21:49 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  206 May 26 21:49 precise-dell.list
-rw-r--r-- 1 root root  138 May 26 21:49 precise-dell.list.distUpgrade

```

at the end of autoremove i got
```

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]


```

---

### Post by zhenia on 2015-09-06
the system problem popups have not been reappearing after all the cleaning, for now at least, but the problem with being unable to install the streamer plug-in for firefox because of package discrepancies remains.

---

### Post by ian-weisser on 2015-09-06
> **zhenia said:**
> The following packages have unmet dependencies:

gstreamer1.0-libav: Depends: libavcodec-extra-54 (>= 6:9.13) but 6:9.18-0ubuntu0.14.04.1 is to be installed
                    Depends: libavformat54 (>= 6:9.1-1) but 6:9.18-0ubuntu0.14.04.1 is to be installed
                    Depends: libavutil52 (>= 6:9.1-1) but 6:9.18-0ubuntu0.14.04.1 is to be installed
                    Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.6 is to be installed
                    Depends: libglib2.0-0 (>= 2.37.3) but 2.40.2-0ubuntu1 is to be installed

Your system is trying to warn you that you have done something most unwise for a beginner -- you seem to have installed non-Ubuntu software from non-Ubuntu sources, and broken your package manager. Whatever you added has a *version conflict* with your release of Ubuntu, meaning it's incompatible.

The package manager is very clever...but not very smart about humans; it has no idea which of the two incompatible options you prefer (Ubuntu or non-Ubuntu gstreamer1.0-libav). So it's asking it's supervisor (you) to resolve the crisis.

Your system may be unable to install/uninstall software, including security updates, until you fix it.
Fixing the problem is usually quite simple.

Here's how you fix it. Do the steps in order. Do not skip steps. If you have a question, or see an error message, post it here before proceeding:
1) Delete those sources. How you delete them depends on how you added them. Only you can tell us that.
2) Uninstall the non-Ubuntu software. (sudo apt-get remove gstreamer1.0-libav). Write down any other packages that the package manager removes with gstreamer1.0-libav!
3) Uninstall the dependencies from that non-Ubuntu source (sudo apt-get autoremove)
4) Clear your package cache of the non-Ubuntu software. (sudo apt-get clean)
5) Rebuild your package database without the non-Ubuntu software (sudo apt-get update)
6) Test your working system for errors (sudo apt-get upgrade)
7) Install the Ubuntu version of the software (sudo apt-get install gstreamer1.0-libav)

---

### Post by zhenia on 2015-09-07
I do have a question.
I do not know what to delete either (step 1). I do not think to have added anything particular; the only thing I manually installed a couple of days ago was "shutter" for screenshots, but it was in the ubuntu software centre. I did not add any sources consciously. Is step 1 skippable?
I did try steps 2-3 but they do not seem to lead anywhere:
```

sudo apt-get remove gstreamer1.0-libav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gstreamer1.0-libav' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
```

---

### Post by zhenia on 2015-09-07
I have proceeded with the following steps 4-7 and the streamer runs fine.
Should I hope that the package manager is back to normal?
Thanks Ian!

---

### Post by ian-weisser on 2015-09-07
> **zhenia said:**
> I did not add any sources consciously. Is step 1 skippable?
Step 1 is usually the most important step, and should not be skipped. The other steps do little without Step 1.
Ubuntu is tested specifically to prevent the type of version incompatibility you seemed to have.
Your package manager seems to work now, but it seems unlikely that my instructions caused that.

Should your problem recur, please post the contents of your /etc/apt/sources.list file, and the list of files within your /etc/apt/sources.list.d/ directory.

---

### Post by Geoffrey_Arndt on 2015-09-07
If you are running Trusty Tahr, then why do you have Precise Pangolin repositories enabled?.   That can corrupt your Ubuntu base system.

---

### Post by tgalati4 on 2015-09-08
Good call.  Was this a Dell with Ubuntu installed?  Try removing those old Dell/Precise repository files, then:

```
sudo apt-get dist-upgrade
```

That should fix a few more things.

---

### Post by zhenia on 2015-09-08
Thank you all so much for helping me out!
Yes this is a Dell laptop but the dist-upgrade seem to tell me that there are no problems to fix?

```

sudo apt-get dist-upgrade


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The Precise files are still there though, in the etc/app directory:

here I have - google-chrome.list; google-chrome.list.distUpgrade; precise-dell.list; precise-dell.list.distUpgrade


```

cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://archive.ubuntu.com/ubuntu/ trusty universe
deb http://archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main



deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


```

---

