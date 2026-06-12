---
title: "Can't compile - weird errors"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by fizgig on 2005-03-16
Is there a list of packages that you ought to have installed to make sure you have everything you need to compile most things you'll encounter?

I'm trying to compile the winmodem driver slmodem and I was able to on my last install of Ubuntu-Hoary but I just reinstalled and now I can't.  Here's my error messages if it helps:

make -C modem all
make[1]: Entering directory `/home/matt/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_main.o -c modem_main.c
modem_main.c:64:28: alsa/asoundlib.h: No such file or directory
modem_main.c:102: error: syntax error before "snd_pcm_t"
modem_main.c:102: warning: no semicolon at end of struct or union
modem_main.c:103: warning: type defaults to `int' in declaration of `chandle'
modem_main.c:103: warning: data definition has no type or storage class
modem_main.c:108: error: syntax error before '}' token
modem_main.c:125: error: syntax error before '*' token
modem_main.c:125: warning: type defaults to `int' in declaration of `dbg_out'
modem_main.c:125: warning: data definition has no type or storage class
modem_main.c: In function `alsa_device_setup':
modem_main.c:129: error: storage size of `pfd' isn't known
modem_main.c:131: error: dereferencing pointer to incomplete type
modem_main.c:131: error: dereferencing pointer to incomplete type
modem_main.c:131: error: dereferencing pointer to incomplete type
modem_main.c:131: error: dereferencing pointer to incomplete type
modem_main.c:131: error: dereferencing pointer to incomplete type
modem_main.c:131: error: dereferencing pointer to incomplete type
modem_main.c:132: warning: implicit declaration of function `snd_pcm_open'
modem_main.c:132: error: dereferencing pointer to incomplete type
modem_main.c:132: error: `SND_PCM_STREAM_PLAYBACK' undeclared (first use in this function)
modem_main.c:132: error: (Each undeclared identifier is reported only once
modem_main.c:132: error: for each function it appears in.)
modem_main.c:132: error: `SND_PCM_NONBLOCK' undeclared (first use in this function)
modem_main.c:134: warning: implicit declaration of function `snd_strerror'
modem_main.c:134: warning: format argument is not a pointer (arg 4)
modem_main.c:138: error: dereferencing pointer to incomplete type
modem_main.c:138: error: `SND_PCM_STREAM_CAPTURE' undeclared (first use in this function)
modem_main.c:140: warning: format argument is not a pointer (arg 4)
modem_main.c:144: warning: implicit declaration of function `snd_pcm_poll_descriptors'
modem_main.c:144: error: dereferencing pointer to incomplete type
modem_main.c:146: warning: format argument is not a pointer (arg 4)
modem_main.c:150: error: dereferencing pointer to incomplete type
modem_main.c:151: error: dereferencing pointer to incomplete type
modem_main.c:154: warning: implicit declaration of function `snd_output_stdio_attach'
modem_main.c:129: warning: unused variable `pfd'
modem_main.c: In function `alsa_device_release':
modem_main.c:161: warning: implicit declaration of function `snd_pcm_close'
modem_main.c:161: error: dereferencing pointer to incomplete type
modem_main.c:162: error: dereferencing pointer to incomplete type
modem_main.c: In function `alsa_xrun_recovery':
modem_main.c:172: warning: implicit declaration of function `snd_pcm_prepare'
modem_main.c:172: error: dereferencing pointer to incomplete type
modem_main.c:174: warning: format argument is not a pointer (arg 3)
modem_main.c:177: error: dereferencing pointer to incomplete type
modem_main.c:178: warning: implicit declaration of function `snd_pcm_format_set_silence'
modem_main.c:178: error: `SND_PCM_FORMAT_S16_LE' undeclared (first use in this function)
modem_main.c:179: warning: implicit declaration of function `snd_pcm_writei'
modem_main.c:179: error: dereferencing pointer to incomplete type
modem_main.c:181: warning: format argument is not a pointer (arg 3)
modem_main.c:184: warning: implicit declaration of function `snd_pcm_start'
modem_main.c:184: error: dereferencing pointer to incomplete type
modem_main.c:186: warning: format argument is not a pointer (arg 3)
modem_main.c: In function `alsa_device_read':
modem_main.c:198: warning: implicit declaration of function `snd_pcm_readi'
modem_main.c:198: error: dereferencing pointer to incomplete type
modem_main.c:205: error: dereferencing pointer to incomplete type
modem_main.c: In function `alsa_device_write':
modem_main.c:215: error: dereferencing pointer to incomplete type
modem_main.c:218: error: dereferencing pointer to incomplete type
modem_main.c:233: error: dereferencing pointer to incomplete type
modem_main.c: At top level:
modem_main.c:240: error: syntax error before "mdm2snd_format"
modem_main.c:241: warning: return type defaults to `int'
modem_main.c: In function `mdm2snd_format':
modem_main.c:243: error: `SND_PCM_FORMAT_S16_LE' undeclared (first use in this function)
modem_main.c:244: error: `SND_PCM_FORMAT_UNKNOWN' undeclared (first use in this function)
modem_main.c: At top level:
modem_main.c:248: error: syntax error before '*' token
modem_main.c: In function `setup_stream':
modem_main.c:250: error: `m' undeclared (first use in this function)
modem_main.c:251: error: `snd_pcm_hw_params_t' undeclared (first use in this function)
modem_main.c:251: error: `hw_params' undeclared (first use in this function)
modem_main.c:252: error: `snd_pcm_sw_params_t' undeclared (first use in this function)
modem_main.c:252: error: `sw_params' undeclared (first use in this function)
modem_main.c:253: error: `snd_pcm_format_t' undeclared (first use in this function)
modem_main.c:253: error: syntax error before "format"
modem_main.c:255: error: `snd_pcm_uframes_t' undeclared (first use in this function)
modem_main.c:255: error: syntax error before "size"
modem_main.c:258: warning: implicit declaration of function `snd_pcm_hw_params_malloc'
modem_main.c:260: error: `stream_name' undeclared (first use in this function)
modem_main.c:260: warning: format argument is not a pointer (arg 4)
modem_main.c:263: warning: implicit declaration of function `snd_pcm_hw_params_any'
modem_main.c:263: error: `handle' undeclared (first use in this function)
modem_main.c:265: warning: format argument is not a pointer (arg 4)
modem_main.c:268: warning: implicit declaration of function `snd_pcm_hw_params_set_access'
modem_main.c:268: error: `SND_PCM_ACCESS_RW_INTERLEAVED' undeclared (first use in this function)
modem_main.c:270: warning: format argument is not a pointer (arg 4)
modem_main.c:273: error: `format' undeclared (first use in this function)
modem_main.c:274: error: `SND_PCM_FORMAT_UNKNOWN' undeclared (first use in this function)
modem_main.c:278: warning: implicit declaration of function `snd_pcm_hw_params_set_format'
modem_main.c:280: warning: format argument is not a pointer (arg 4)
modem_main.c:283: warning: implicit declaration of function `snd_pcm_hw_params_set_channels'
modem_main.c:285: warning: format argument is not a pointer (arg 4)
modem_main.c:289: warning: implicit declaration of function `snd_pcm_hw_params_set_rate_near'
modem_main.c:291: warning: format argument is not a pointer (arg 4)
modem_main.c:299: error: `rsize' undeclared (first use in this function)
modem_main.c:299: error: `size' undeclared (first use in this function)
modem_main.c:299: error: dereferencing pointer to incomplete type
modem_main.c:300: warning: implicit declaration of function `snd_pcm_hw_params_set_period_size_near'
modem_main.c:302: warning: format argument is not a pointer (arg 4)
modem_main.c:311: warning: implicit declaration of function `snd_pcm_hw_params_set_buffer_size_near'
modem_main.c:313: warning: format argument is not a pointer (arg 4)
modem_main.c:320: warning: implicit declaration of function `snd_pcm_hw_params'
modem_main.c:322: warning: format argument is not a pointer (arg 4)
modem_main.c:327: warning: format argument is not a pointer (arg 4)
modem_main.c:330: warning: implicit declaration of function `snd_pcm_hw_params_free'
modem_main.c:332: warning: implicit declaration of function `snd_pcm_sw_params_malloc'
modem_main.c:334: warning: format argument is not a pointer (arg 4)
modem_main.c:337: warning: implicit declaration of function `snd_pcm_sw_params_current'
modem_main.c:339: warning: format argument is not a pointer (arg 4)
modem_main.c:342: warning: implicit declaration of function `snd_pcm_sw_params_set_start_threshold'
modem_main.c:344: warning: format argument is not a pointer (arg 4)
modem_main.c:347: warning: implicit declaration of function `snd_pcm_sw_params_set_avail_min'
modem_main.c:349: warning: format argument is not a pointer (arg 4)
modem_main.c:352: warning: implicit declaration of function `snd_pcm_sw_params_set_xfer_align'
modem_main.c:354: warning: format argument is not a pointer (arg 4)
modem_main.c:357: warning: implicit declaration of function `snd_pcm_sw_params'
modem_main.c:359: warning: format argument is not a pointer (arg 4)
modem_main.c:362: warning: implicit declaration of function `snd_pcm_sw_params_free'
modem_main.c:365: warning: implicit declaration of function `snd_pcm_dump'
modem_main.c: In function `alsa_start':
modem_main.c:374: error: dereferencing pointer to incomplete type
modem_main.c:375: error: dereferencing pointer to incomplete type
modem_main.c:378: error: dereferencing pointer to incomplete type
modem_main.c:381: error: dereferencing pointer to incomplete type
modem_main.c:384: error: `SND_PCM_FORMAT_S16_LE' undeclared (first use in this function)
modem_main.c:390: error: dereferencing pointer to incomplete type
modem_main.c:395: error: dereferencing pointer to incomplete type
modem_main.c:396: error: dereferencing pointer to incomplete type
modem_main.c:397: warning: implicit declaration of function `snd_pcm_link'
modem_main.c:397: error: dereferencing pointer to incomplete type
modem_main.c:397: error: dereferencing pointer to incomplete type
modem_main.c:399: warning: format argument is not a pointer (arg 3)
modem_main.c:402: error: dereferencing pointer to incomplete type
modem_main.c:404: warning: format argument is not a pointer (arg 3)
modem_main.c:407: error: dereferencing pointer to incomplete type
modem_main.c: In function `alsa_stop':
modem_main.c:415: error: dereferencing pointer to incomplete type
modem_main.c:416: warning: implicit declaration of function `snd_pcm_drop'
modem_main.c:416: error: dereferencing pointer to incomplete type
modem_main.c:417: warning: implicit declaration of function `snd_pcm_nonblock'
modem_main.c:417: error: dereferencing pointer to incomplete type
modem_main.c:418: warning: implicit declaration of function `snd_pcm_drain'
modem_main.c:418: error: dereferencing pointer to incomplete type
modem_main.c:419: error: dereferencing pointer to incomplete type
modem_main.c:420: warning: implicit declaration of function `snd_pcm_unlink'
modem_main.c:420: error: dereferencing pointer to incomplete type
modem_main.c:421: warning: implicit declaration of function `snd_pcm_hw_free'
modem_main.c:421: error: dereferencing pointer to incomplete type
modem_main.c:422: error: dereferencing pointer to incomplete type
modem_main.c: In function `alsa_ioctl':
modem_main.c:439: error: dereferencing pointer to incomplete type
modem_main.c:440: error: dereferencing pointer to incomplete type
modem_main.c: In function `modemap_start':
modem_main.c:469: error: dereferencing pointer to incomplete type
modem_main.c:470: error: dereferencing pointer to incomplete type
modem_main.c:475: error: dereferencing pointer to incomplete type
modem_main.c:477: error: dereferencing pointer to incomplete type
modem_main.c:480: error: dereferencing pointer to incomplete type
modem_main.c: In function `modemap_stop':
modem_main.c:488: error: dereferencing pointer to incomplete type
modem_main.c: In function `modemap_ioctl':
modem_main.c:498: error: dereferencing pointer to incomplete type
modem_main.c:501: error: dereferencing pointer to incomplete type
modem_main.c: In function `mdm_device_read':
modem_main.c:517: error: dereferencing pointer to incomplete type
modem_main.c: In function `mdm_device_write':
modem_main.c:524: error: dereferencing pointer to incomplete type
modem_main.c: In function `mdm_device_setup':
modem_main.c:533: error: dereferencing pointer to incomplete type
modem_main.c:533: error: dereferencing pointer to incomplete type
modem_main.c:533: error: dereferencing pointer to incomplete type
modem_main.c:533: error: dereferencing pointer to incomplete type
modem_main.c:533: error: dereferencing pointer to incomplete type
modem_main.c:533: error: dereferencing pointer to incomplete type
modem_main.c:549: error: dereferencing pointer to incomplete type
modem_main.c:550: error: dereferencing pointer to incomplete type
modem_main.c: In function `mdm_device_release':
modem_main.c:556: error: dereferencing pointer to incomplete type
modem_main.c: In function `modem_run':
modem_main.c:694: error: dereferencing pointer to incomplete type
modem_main.c:694: error: dereferencing pointer to incomplete type
modem_main.c:696: error: dereferencing pointer to incomplete type
modem_main.c:696: error: dereferencing pointer to incomplete type
modem_main.c:697: error: dereferencing pointer to incomplete type
modem_main.c:721: error: dereferencing pointer to incomplete type
modem_main.c:721: error: dereferencing pointer to incomplete type
modem_main.c:730: error: dereferencing pointer to incomplete type
modem_main.c:739: error: dereferencing pointer to incomplete type
modem_main.c:739: error: dereferencing pointer to incomplete type
modem_main.c:753: error: dereferencing pointer to incomplete type
modem_main.c:760: error: dereferencing pointer to incomplete type
modem_main.c:787: error: dereferencing pointer to incomplete type
modem_main.c: In function `modem_main':
modem_main.c:852: error: storage size of `device' isn't known
modem_main.c:852: warning: unused variable `device'
make[1]: *** [modem_main.o] Error 1
make[1]: Leaving directory `/home/matt/slmodem-2.9.10/modem'
make: *** [modem] Error 2

---

### Post by Xian on 2005-03-17
[QUOTE=fizgig]Is there a list of packages that you ought to have installed to make sure you have everything you need to compile most things you'll encounter?[/QUOTE]
sudo apt-get install build-essential

---

### Post by fizgig on 2005-03-17
Well, I do have that package installed.  Can anyone see what else I might be doing wrong to get these error messages?

---

### Post by gazmon on 2006-12-28
You need  libasound2-dev that provides alsa headers:
```
sudo apt-get install libasound2-dev
```

---

