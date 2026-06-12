---
title: "problems with update manager"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by zhenia on 2015-10-13
After a recent update the
update manager (launched with sudo update-manager -d)
gets me
"failed to download repository information"
apt-get works ok
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
anything of concern?

the message system error detected keeps popping up, too

---

### Post by oldos2er on 2015-10-13
What version of Ubuntu are you running?

---

### Post by zhenia on 2015-10-13
14.04

---

### Post by zhenia on 2015-10-13
must say that i had to force shut down earlier on, could that have caused the problem?
on restarting i noticed that there is an error message coming on boot
just in case it helps here is the crash report
```
ProblemType: Package
DKMSBuildLog:
 DKMS make.log for alsa-hda-0.1.1somerville for kernel 3.13.0-65-generic (x86_64)
 Wed Oct 14 00:48:56 CEST 2015
 make -C /lib/modules/3.13.0-65-generic/build M=/var/lib/dkms/alsa-hda/0.1.1somerville/build modules
 make[1]: Entering directory `/usr/src/linux-headers-3.13.0-65-generic'
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
 make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-65-generic'
 make: *** [all] Error 2
DKMSKernelVersion: 3.13.0-65-generic
Date: Wed Oct 14 00:49:01 2015
DuplicateSignature: dkms:alsa-hda-dkms:0.1.1somerville:/var/lib/dkms/alsa-hda/0.1.1somerville/build/hda_codec.h:48:8: error: redeclaration of enumerator &#8216;SND_PR_ALWAYS&#8217;
Package: alsa-hda-dkms 0.1.1somerville
PackageVersion: 0.1.1somerville
SourcePackage: dkms-hda
Title: alsa-hda-dkms 0.1.1somerville: alsa-hda kernel module failed to build
```

---

### Post by grahammechanical on 2015-10-13
The message "failed to download repository information" will appear even if only one repository is not available. Running

```
sudo apt-get update
```

will usually show what URLs (repositories) apt-get cannot connect to. The apt-get listing will show "Hit" for active repositories and "Err" for repositories that are not available. It does not necessarily mean that the regular update/upgrade will not work. Unless for some reason connection is not being made to any repositories. In this case Update Manager (the GUI version) will claim that the OS is up to date.

Regards.

Regards

---

### Post by zhenia on 2015-10-14
this morning it seems to have gotten back to normal, sorry for having disturbed! No idea what the bug was.
all seems ok here
```
sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com trusty InRelease                   
Ign http://archive.ubuntu.com trusty InRelease                       
Hit http://security.ubuntu.com trusty-security InRelease             
Hit http://dl.google.com stable Release.gpg                          
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com trusty Release                                
Hit http://archive.ubuntu.com trusty-backports InRelease                       
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.ubuntu.com trusty-updates/main Sources                      
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.ubuntu.com trusty-updates/restricted Sources                
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://archive.ubuntu.com trusty-updates/universe Sources                  
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources                
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages     
Ign http://dl.google.com stable/main Translation-en                 
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en  
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en  
Hit http://archive.ubuntu.com trusty-updates/main Translation-en          
Hit http://security.ubuntu.com trusty-security/restricted Translation-en  
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en    
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-backports/main Sources
Hit http://archive.ubuntu.com trusty-backports/restricted Sources
Hit http://archive.ubuntu.com trusty-backports/universe Sources
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty Release      
Hit http://archive.ubuntu.com trusty/main Sources
Hit http://archive.ubuntu.com trusty/restricted Sources
Hit http://archive.ubuntu.com trusty/universe Sources
Hit http://archive.ubuntu.com trusty/multiverse Sources
Hit http://archive.ubuntu.com trusty/main amd64 Packages
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done 

```

---

