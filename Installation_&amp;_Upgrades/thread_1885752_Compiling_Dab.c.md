---
title: "Compiling Dab.c"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by Zee818 on 2011-11-23
Hi, I am having problems on my debian compiling dab.c, a software that is suppose to convert audio magnetic strip data to binary. when i try and compile it i get the following errors.

gcc dab.c -o dab -lsndfile
In file included from dab.c:21:
/home/zee/Downloads/sndfile.h:233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_count_t’
/home/zee/Downloads/sndfile.h:243: error: expected specifier-qualifier-list before ‘sf_count_t’
/home/zee/Downloads/sndfile.h:296: error: expected specifier-qualifier-list before ‘sf_count_t’
/home/zee/Downloads/sndfile.h:390: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_seek’
/home/zee/Downloads/sndfile.h:407: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_read_raw’
/home/zee/Downloads/sndfile.h:408: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_write_raw’
/home/zee/Downloads/sndfile.h:420: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_readf_short’
/home/zee/Downloads/sndfile.h:421: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_writef_short’
/home/zee/Downloads/sndfile.h:423: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_readf_int’
/home/zee/Downloads/sndfile.h:424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_writef_int’
/home/zee/Downloads/sndfile.h:426: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_readf_float’
/home/zee/Downloads/sndfile.h:427: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_writef_float’
/home/zee/Downloads/sndfile.h:429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_readf_double’
/home/zee/Downloads/sndfile.h:430: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_writef_double’
/home/zee/Downloads/sndfile.h:437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_read_short’
/home/zee/Downloads/sndfile.h:438: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_write_short’
/home/zee/Downloads/sndfile.h:440: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_read_int’
/home/zee/Downloads/sndfile.h:441: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_write_int’
/home/zee/Downloads/sndfile.h:443: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_read_float’
/home/zee/Downloads/sndfile.h:444: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_write_float’
/home/zee/Downloads/sndfile.h:446: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_read_double’
/home/zee/Downloads/sndfile.h:447: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sf_write_double’
dab.c: In function ‘sndfile_init’:
dab.c:290: error: ‘SF_INFO’ has no member named ‘frames’
dab.c:290: error: ‘SF_INFO’ has no member named ‘samplerate’
dab.c:290: error: ‘SF_INFO’ has no member named ‘channels’
dab.c:291: error: ‘SF_INFO’ has no member named ‘format’
dab.c:291: error: ‘SF_INFO’ has no member named ‘sections’
dab.c:291: error: ‘SF_INFO’ has no member named ‘seekable’
dab.c:294: error: ‘SF_INFO’ has no member named ‘channels’
dab.c:299: error: ‘SF_INFO’ has no member named ‘frames’
dab.c: In function ‘get_sndfile’:
dab.c:311: error: ‘sf_count_t’ undeclared (first use in this function)
dab.c:311: error: (Each undeclared identifier is reported only once
dab.c:311: error: for each function it appears in.)
dab.c:311: error: expected ‘;’ before ‘count’
dab.c:315: error: ‘count’ undeclared (first use in this function)
root@Bank:/home/zee/Downloads# 

anyone know what that is from? i would appreciate the help i am kind of new to compiling in linux. thank you

---

