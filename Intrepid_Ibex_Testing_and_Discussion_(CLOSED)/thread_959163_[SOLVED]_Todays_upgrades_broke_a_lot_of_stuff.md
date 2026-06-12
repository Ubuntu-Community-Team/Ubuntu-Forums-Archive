---
title: "[SOLVED] Todays upgrades broke a lot of stuff"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by amano on 2008-10-26
Is it just me? but after the updates of today a lot of stuff severely broke:

1) Orca showed up in the main menu. I tried to edit the menu but that didn't work. Instead the main menu will not open at all anymore (just places and system)

2) My firefox bookmarks don't show up anymore (firefox is a problem already for some time because it always starts up fullscreen for me, just hitting F11 twice will give me a normal window).

3) Pidin will not start up anymore:

```
amano@desktop:~$ pidgin
*** glibc detected *** pidgin: double free or corruption (out): 0x09958f10 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76e93f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb76eb456]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7922c06]
/usr/lib/libglib-2.0.so.0(g_string_free+0x5c)[0xb793f00c]
/usr/lib/pidgin/nautilus.so[0xb6fd927a]
/usr/lib/libpurple.so.0(purple_marshal_VOID__POINTER+0x28)[0xb786b713]
/usr/lib/libpurple.so.0(purple_signal_emit_vargs+0x168)[0xb786b2d5]
/usr/lib/libpurple.so.0(purple_signal_emit+0x81)[0xb786b167]
/usr/lib/libpurple.so.0(purple_blist_update_buddy_status+0xd5)[0xb7822d38]
/usr/lib/libpurple.so.0(purple_prpl_got_user_status+0x16e)[0xb7860e6d]
/usr/lib/purple-2/liboscar.so.0[0xb562011a]
/usr/lib/purple-2/liboscar.so.0[0xb56018f0]
/usr/lib/purple-2/liboscar.so.0[0xb56019eb]
/usr/lib/purple-2/liboscar.so.0[0xb561726c]
/usr/lib/purple-2/liboscar.so.0[0xb56174fc]
/usr/lib/purple-2/liboscar.so.0(flap_connection_recv_cb+0x2d6)[0xb56177fd]
pidgin[0x80ad7bf]
/usr/lib/libglib-2.0.so.0[0xb79516fd]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb791a6f8]
/usr/lib/libglib-2.0.so.0[0xb791dda3]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2)[0xb791e2c2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7c293a9]
pidgin(main+0xc78)[0x80caaaf]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7690685]
pidgin[0x806d8b1]
======= Memory map: ========
08048000-0811d000 r-xp 00000000 08:02 274234     /usr/bin/pidgin
0811d000-0811e000 r--p 000d4000 08:02 274234     /usr/bin/pidgin
0811e000-08121000 rw-p 000d5000 08:02 274234     /usr/bin/pidgin
095b5000-0a023000 rw-p 095b5000 00:00 0          [heap]
b323c000-b3240000 r-xp 00000000 08:02 323726     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b3240000-b3241000 r--p 00003000 08:02 323726     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b3241000-b3242000 rw-p 00004000 08:02 323726     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b3242000-b32a2000 rw-s 00000000 00:09 3014721    /SYSV00000000 (deleted)
b32a2000-b33a6000 rw-p b32a2000 00:00 0 
b33a6000-b3425000 r--p 00000000 08:02 467736     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansCondensed-Bold.ttf
b3425000-b3426000 r-xp 00000000 08:02 280324     /usr/lib/gconv/ISO8859-1.so
b3426000-b3427000 r--p 00001000 08:02 280324     /usr/lib/gconv/ISO8859-1.so
b3427000-b3428000 rw-p 00002000 08:02 280324     /usr/lib/gconv/ISO8859-1.so
b3428000-b3501000 rw-p b3428000 00:00 0 
b3501000-b3540000 r-xp 00000000 08:02 274348     /usr/lib/libhunspell-1.2.so.0.0.0
b3540000-b3541000 r--p 0003e000 08:02 274348     /usr/lib/libhunspell-1.2.so.0.0.0
b3541000-b3545000 rw-p 0003f000 08:02 274348     /usr/lib/libhunspell-1.2.so.0.0.0
b354e000-b3553000 r-xp 00000000 08:02 323627     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3553000-b3554000 r--p 00004000 08:02 323627     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3554000-b3555000 rw-p 00005000 08:02 323627     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3555000-b3559000 r-xp 00000000 08:02 322881     /usr/lib/enchant/libenchant_myspell.so
b3559000-b355a000 r--p 00003000 08:02 322881     /usr/lib/enchant/libenchant_myspell.so
b355a000-b355b000 rw-p 00004000 08:02 322881     /usr/lib/enchant/libenchant_myspell.so
b355b000-b3566000 r-xp 00000000 08:02 322878     /usr/lib/enchant/libenchant_ispell.so
b3566000-b3567000 r--p 0000a000 08:02 322878     /usr/lib/enchant/libenchant_ispell.so
b3567000-b3568000 rw-p 0000b000 08:02 322878     /usr/lib/enchant/libenchant_ispell.so
b3568000-b35fc000 r-xp 00000000 08:02 501438     /usr/lib/libaspell.so.15.1.4
b35fc000-b35ff000 r--p 00093000 08:02 501438     /usr/lib/libaspell.so.15.1.4
b35ff000-b3600000 rw-p 00096000 08:02 501438     /usr/lib/libaspell.so.15.1.4
b3600000-b3604000 rw-p b3600000 00:00 0 
b3605000-b3607000 r-xp 00000000 08:02 322972     /usr/lib/enchant/libenchant_zemberek.so
b3607000-b3608000 r--p 00001000 08:02 322972     /usr/lib/enchant/libenchant_zemberek.so
b3608000-b3609000 rw-p 00002000 08:02 322972     /usr/lib/enchant/libenchant_zemberek.so
b3609000-b3611000 r-xp 00000000 08:02 322706     /usr/lib/enchant/libenchant_hspell.so
b3611000-b3612000 r--p 00007000 08:02 322706     /usr/lib/enchant/libenchant_hspell.so
b3612000-b3614000 rw-p 00008000 08:02 322706     /usr/lib/enchant/libenchant_hspell.so
b3614000-b3718000 rw-p b3614000 00:00 0 
b3718000-b371a000 r-xp 00000000 08:02 277873     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b371a000-b371b000 r--p 00001000 08:02 277873     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b371b000-b371c000 rw-p 00002000 08:02 277873     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b371c000-b379e000 r--p 00000000 08:02 467933     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansCondensed.ttf
b379e000-b37a4000 r--s 00000000 08:02 822851     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b37a4000-b37a5000 r--s 00000000 08:02 824996     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
b37a5000-b37a8000 r--s 00000000 08:02 824967     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b37a8000-b37a9000 r--s 00000000 08:02 824805     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b37a9000-b37ab000 r--s 00000000 08:02 824783     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b37ab000-b37ac000 r--s 00000000 08:02 824777     /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b37ac000-b37ad000 r--s 00000000 08:02 824763     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b37ad000-b37ae000 r--s 00000000 08:02 824747     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b37ae000-b37b2000 r--s 00000000 08:02 824727     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b37b2000-b37b4000 r--s 00000000 08:02 824691     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b37b4000-b37b7000 r--s 00000000 08:02 824675     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b37b7000-b37b8000 r--s 00000000 08:02 824653     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b37b8000-b37ba000 r--s 00000000 08:02 824648     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b37ba000-b37bd000 r--s 00000000 08:02 824567     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b37bd000-b37bf000 r--s 00000000 08:02 824534     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b37bf000-b37c2000 r--s 00000000 08:02 824460     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b37c2000-b37c9000 r--s 00000000 08:02 824439     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b37c9000-b37cc000 r--s 00000000 08:02 824380     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b37cc000-b37ce000 r--s 00000000 08:02 824324     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b37ce000-b37d6000 r--s 00000000 08:02 824322     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b37d6000-b37e1000 r--s 00000000 08:02 824158     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b37e1000-b3803000 r--s 00000000 08:02 824282     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b3803000-b3806000 r--s 00000000 08:02 824264     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b3806000-b380d000 r--s 00000000 08:02 824262     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b380d000-b3816000 r--s 00000000 08:02 822888     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b3816000-b381d000 r--s 00000000 08:02 822863     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b381d000-b3834000 r--s 00000000 08:02 404871     /usr/share/mime/mime.cache
b3834000-b3acd000 r--p 00000000 08:02 548552     /usr/share/icons/hicolor/icon-theme.cache
b3acd000-b41ab000 r--p 00000000 08:02 548362     /usr/share/icons/gnome/icon-theme.cache
b41ab000-b4256000 r--p 00000000 08:02 548758     /usr/share/icons/Tangerine/icon-theme.cache
b4256000-b43c5000 r--p 00000000 08:02 419720     /usr/share/icons/Human/icon-theme.cache
b43c5000-b43cb000 r-xp 00000000 08:02 280899     /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b43cb000-b43cc000 r--p 00005000 08:02 280899     /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b43cc000-b43cd000 rw-p 00006000 08:02 280899     /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b43cd000-bAborted

```

Ubuntu is due to be released and it is in worse shape than alpha 5 for me now (e.g. DVD playback is rather unusable with totem gstreamer now). Can somebody confirm some of my issues?

---

### Post by mickbuntu on 2008-10-26
Hello, after updating:

1. Pidgin works I just turned it on.

2.  Firefox is ok, except it does have a bookmark click bug. But favourites still show once selecting correct spot (none default theme bug?).

3. Have not tried Orca the kde ones better though kmouth and ksayit.

4. Cache corruption though on  apt-get files went away after refresh (think)

> **amano said:**
> Is it just me? but after the updates of today a lot of stuff severely broke:

1) Orca showed up in the main menu. I tried to edit the menu but that didn't work. Instead the main menu will not open at all anymore (just places and system)

2) My firefox bookmarks don't show up anymore (firefox is a problem already for some time because it always starts up fullscreen for me, just hitting F11 twice will give me a normal window).

3) Pidin will not start up anymore:

```
amano@desktop:~$ pidgin
*** glibc detected *** pidgin: double free or corruption (out): 0x09958f10 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76e93f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb76eb456]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7922c06]
/usr/lib/libglib-2.0.so.0(g_string_free+0x5c)[0xb793f00c]
/usr/lib/pidgin/nautilus.so[0xb6fd927a]
/usr/lib/libpurple.so.0(purple_marshal_VOID__POINTER+0x28)[0xb786b713]
/usr/lib/libpurple.so.0(purple_signal_emit_vargs+0x168)[0xb786b2d5]
/usr/lib/libpurple.so.0(purple_signal_emit+0x81)[0xb786b167]
/usr/lib/libpurple.so.0(purple_blist_update_buddy_status+0xd5)[0xb7822d38]
/usr/lib/libpurple.so.0(purple_prpl_got_user_status+0x16e)[0xb7860e6d]
/usr/lib/purple-2/liboscar.so.0[0xb562011a]
/usr/lib/purple-2/liboscar.so.0[0xb56018f0]
/usr/lib/purple-2/liboscar.so.0[0xb56019eb]
/usr/lib/purple-2/liboscar.so.0[0xb561726c]
/usr/lib/purple-2/liboscar.so.0[0xb56174fc]
/usr/lib/purple-2/liboscar.so.0(flap_connection_recv_cb+0x2d6)[0xb56177fd]
pidgin[0x80ad7bf]
/usr/lib/libglib-2.0.so.0[0xb79516fd]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb791a6f8]
/usr/lib/libglib-2.0.so.0[0xb791dda3]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2)[0xb791e2c2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7c293a9]
pidgin(main+0xc78)[0x80caaaf]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7690685]
pidgin[0x806d8b1]
======= Memory map: ========
08048000-0811d000 r-xp 00000000 08:02 274234     /usr/bin/pidgin
0811d000-0811e000 r--p 000d4000 08:02 274234     /usr/bin/pidgin
0811e000-08121000 rw-p 000d5000 08:02 274234     /usr/bin/pidgin
095b5000-0a023000 rw-p 095b5000 00:00 0          [heap]
b323c000-b3240000 r-xp 00000000 08:02 323726     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b3240000-b3241000 r--p 00003000 08:02 323726     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b3241000-b3242000 rw-p 00004000 08:02 323726     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b3242000-b32a2000 rw-s 00000000 00:09 3014721    /SYSV00000000 (deleted)
b32a2000-b33a6000 rw-p b32a2000 00:00 0 
b33a6000-b3425000 r--p 00000000 08:02 467736     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansCondensed-Bold.ttf
b3425000-b3426000 r-xp 00000000 08:02 280324     /usr/lib/gconv/ISO8859-1.so
b3426000-b3427000 r--p 00001000 08:02 280324     /usr/lib/gconv/ISO8859-1.so
b3427000-b3428000 rw-p 00002000 08:02 280324     /usr/lib/gconv/ISO8859-1.so
b3428000-b3501000 rw-p b3428000 00:00 0 
b3501000-b3540000 r-xp 00000000 08:02 274348     /usr/lib/libhunspell-1.2.so.0.0.0
b3540000-b3541000 r--p 0003e000 08:02 274348     /usr/lib/libhunspell-1.2.so.0.0.0
b3541000-b3545000 rw-p 0003f000 08:02 274348     /usr/lib/libhunspell-1.2.so.0.0.0
b354e000-b3553000 r-xp 00000000 08:02 323627     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3553000-b3554000 r--p 00004000 08:02 323627     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3554000-b3555000 rw-p 00005000 08:02 323627     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3555000-b3559000 r-xp 00000000 08:02 322881     /usr/lib/enchant/libenchant_myspell.so
b3559000-b355a000 r--p 00003000 08:02 322881     /usr/lib/enchant/libenchant_myspell.so
b355a000-b355b000 rw-p 00004000 08:02 322881     /usr/lib/enchant/libenchant_myspell.so
b355b000-b3566000 r-xp 00000000 08:02 322878     /usr/lib/enchant/libenchant_ispell.so
b3566000-b3567000 r--p 0000a000 08:02 322878     /usr/lib/enchant/libenchant_ispell.so
b3567000-b3568000 rw-p 0000b000 08:02 322878     /usr/lib/enchant/libenchant_ispell.so
b3568000-b35fc000 r-xp 00000000 08:02 501438     /usr/lib/libaspell.so.15.1.4
b35fc000-b35ff000 r--p 00093000 08:02 501438     /usr/lib/libaspell.so.15.1.4
b35ff000-b3600000 rw-p 00096000 08:02 501438     /usr/lib/libaspell.so.15.1.4
b3600000-b3604000 rw-p b3600000 00:00 0 
b3605000-b3607000 r-xp 00000000 08:02 322972     /usr/lib/enchant/libenchant_zemberek.so
b3607000-b3608000 r--p 00001000 08:02 322972     /usr/lib/enchant/libenchant_zemberek.so
b3608000-b3609000 rw-p 00002000 08:02 322972     /usr/lib/enchant/libenchant_zemberek.so
b3609000-b3611000 r-xp 00000000 08:02 322706     /usr/lib/enchant/libenchant_hspell.so
b3611000-b3612000 r--p 00007000 08:02 322706     /usr/lib/enchant/libenchant_hspell.so
b3612000-b3614000 rw-p 00008000 08:02 322706     /usr/lib/enchant/libenchant_hspell.so
b3614000-b3718000 rw-p b3614000 00:00 0 
b3718000-b371a000 r-xp 00000000 08:02 277873     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b371a000-b371b000 r--p 00001000 08:02 277873     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b371b000-b371c000 rw-p 00002000 08:02 277873     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b371c000-b379e000 r--p 00000000 08:02 467933     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansCondensed.ttf
b379e000-b37a4000 r--s 00000000 08:02 822851     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b37a4000-b37a5000 r--s 00000000 08:02 824996     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
b37a5000-b37a8000 r--s 00000000 08:02 824967     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b37a8000-b37a9000 r--s 00000000 08:02 824805     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b37a9000-b37ab000 r--s 00000000 08:02 824783     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b37ab000-b37ac000 r--s 00000000 08:02 824777     /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b37ac000-b37ad000 r--s 00000000 08:02 824763     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b37ad000-b37ae000 r--s 00000000 08:02 824747     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b37ae000-b37b2000 r--s 00000000 08:02 824727     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b37b2000-b37b4000 r--s 00000000 08:02 824691     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b37b4000-b37b7000 r--s 00000000 08:02 824675     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b37b7000-b37b8000 r--s 00000000 08:02 824653     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b37b8000-b37ba000 r--s 00000000 08:02 824648     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b37ba000-b37bd000 r--s 00000000 08:02 824567     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b37bd000-b37bf000 r--s 00000000 08:02 824534     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b37bf000-b37c2000 r--s 00000000 08:02 824460     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b37c2000-b37c9000 r--s 00000000 08:02 824439     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b37c9000-b37cc000 r--s 00000000 08:02 824380     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b37cc000-b37ce000 r--s 00000000 08:02 824324     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b37ce000-b37d6000 r--s 00000000 08:02 824322     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b37d6000-b37e1000 r--s 00000000 08:02 824158     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b37e1000-b3803000 r--s 00000000 08:02 824282     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b3803000-b3806000 r--s 00000000 08:02 824264     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b3806000-b380d000 r--s 00000000 08:02 824262     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b380d000-b3816000 r--s 00000000 08:02 822888     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b3816000-b381d000 r--s 00000000 08:02 822863     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b381d000-b3834000 r--s 00000000 08:02 404871     /usr/share/mime/mime.cache
b3834000-b3acd000 r--p 00000000 08:02 548552     /usr/share/icons/hicolor/icon-theme.cache
b3acd000-b41ab000 r--p 00000000 08:02 548362     /usr/share/icons/gnome/icon-theme.cache
b41ab000-b4256000 r--p 00000000 08:02 548758     /usr/share/icons/Tangerine/icon-theme.cache
b4256000-b43c5000 r--p 00000000 08:02 419720     /usr/share/icons/Human/icon-theme.cache
b43c5000-b43cb000 r-xp 00000000 08:02 280899     /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b43cb000-b43cc000 r--p 00005000 08:02 280899     /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b43cc000-b43cd000 rw-p 00006000 08:02 280899     /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b43cd000-bAborted

```

Ubuntu is due to be released and it is in worse shape than alpha 5 for me now (e.g. DVD playback is rather unusable with totem gstreamer now). Can somebody confirm some of my issues?

---

### Post by danf_1979 on 2008-10-26
Pidgin works fine here, so does firefox. Latest upgrades.

---

### Post by amano on 2008-10-26
Well. I ironed out my problem. I had my harddisc completely full. Sorry. Firefox and Pidgin work now (though Firefox still starting up in fullscreen mode).

I will mark this thread as solved.

EDIT: Just for later reference --> The Firefox fullscreen startup got solved by creating a new Firefox Profile with firefox -ProfileManager and by copying my bookmarks and my passwords over from the old profile.

---

