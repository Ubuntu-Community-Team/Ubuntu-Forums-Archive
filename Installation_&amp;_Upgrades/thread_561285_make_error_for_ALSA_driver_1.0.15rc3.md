---
title: "make error for ALSA driver 1.0.15rc3"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by jasc on 2007-09-27
Hi all,

I need to re-compile ALSA for my lenovo c200 with realtek ALC861-VD, and am running into errors during "make".

I ran ./configure --with-cards=hda-intel that finished, but with this warning in the middle:
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
at the end of the configuration, it said this, which I thought was a bit odd: Hacking autoconf.h...

I went ahead with make, but received this error:
CC [M]  /home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.o
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc_resume’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:1999: warning: implicit declaration of function ‘snd_hda_resume_ctls’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:2001: warning: implicit declaration of function ‘snd_hda_resume_spdif_out’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:2003: warning: implicit declaration of function ‘snd_hda_resume_spdif_in’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc882_mux_enum_put’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:4759: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc883_mux_enum_put’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:5642: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc262_fujitsu_master_sw_put’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:7165: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:7166: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc268_mux_enum_put’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:7962: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc861vd_mux_enum_put’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:9557: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c: In function ‘alc662_mux_enum_put’:
/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.c:10487: error: ‘struct hda_codec’ has no member named ‘in_resume’
make[4]: *** [/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda/patch_realtek.o] Error 1
make[3]: *** [/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci/hda] Error 2
make[2]: *** [/home/karyn/alsa-src/alsa-driver-1.0.15rc3/pci] Error 2
make[1]: *** [_module_/home/karyn/alsa-src/alsa-driver-1.0.15rc3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

Is this a problem with my system, or with build-essential, or Ubuntu? I'd really like to get my sound working, and I've been working to solve this for far too long now. 

Thank you for any help you can give me.

---

