---
title: "Messed up with spell checker, can't start pidgin, problems with evolution"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by mado89 on 2011-09-09
Hi,
i some how (honestly i don't know any more what i did) messed up with the spellcheckers installed on my computer (Ubuntu 11.04)
Now when i want to start pidigin, i get this output: 
(a similar when i try to replay to an email with evolution)
```
*** buffer overflow detected ***: pidgin terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x7fb5f5f291d7]
/lib/x86_64-linux-gnu/libc.so.6(+0xfd0f0)[0x7fb5f5f280f0]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgr8add_wordEPKciiPtiS1_b+0x7b)[0x7fb5d75003bb]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgr11load_tablesEPKcS1_+0x268)[0x7fb5d7500be8]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgrC1EPKcS1_S1_+0xb2)[0x7fb5d7500d82]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN8HunspellC2EPKcS1_S1_+0x8a)[0x7fb5d75010ba]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN14MySpellChecker17requestDictionaryEPKc+0x39d)[0x7fb5d750e4ed]
/usr/local/lib/enchant/libenchant_myspell.so(+0x29656)[0x7fb5d750e656]
/usr/local/lib/libenchant.so.1(+0x41b8)[0x7fb5f3e411b8]
/usr/local/lib/libenchant.so.1(enchant_broker_request_dict+0xc3)[0x7fb5f3e425b3]
/usr/lib/libgtkspell.so.0(+0x4d75)[0x7fb5f8301d75]
/usr/lib/libgtkspell.so.0(gtkspell_new_attach+0xfb)[0x7fb5f8301f7b]
pidgin(pidgin_setup_gtkspell+0x67)[0x4b1507]
pidgin[0x4abe35]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0x573)[0x7fb5f6a13873]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x1076c)[0x7fb5f69f176c]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x299)[0x7fb5f69f4389]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_new_valist+0x1d1)[0x7fb5f69f5321]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_new+0xd1)[0x7fb5f69f5621]
pidgin[0x448bef]
pidgin(main+0x831)[0x481d01]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xff)[0x7fb5f5e49eff]
pidgin[0x430679]
======= Memory map: ========
00400000-004e8000 r-xp 00000000 08:07 180950                             /usr/bin/pidgin
006e7000-006e8000 r--p 000e7000 08:07 180950                             /usr/bin/pidgin
006e8000-006ed000 rw-p 000e8000 08:07 180950                             /usr/bin/pidgin
006ed000-006ee000 rw-p 00000000 00:00 0 
01d99000-02633000 rw-p 00000000 00:00 0                                  [heap]
7fb5d7456000-7fb5d74e5000 rw-p 00000000 00:00 0 
7fb5d74e5000-7fb5d7520000 r-xp 00000000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7fb5d7520000-7fb5d7720000 ---p 0003b000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7fb5d7720000-7fb5d7721000 r--p 0003b000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7fb5d7721000-7fb5d7725000 rw-p 0003c000 08:07 378538                     /usr/local/lib/enchant/libenchant_myspell.so
7fb5d7725000-7fb5d773a000 r-xp 00000000 08:07 35355                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb5d773a000-7fb5d7939000 ---p 00015000 08:07 35355                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb5d7939000-7fb5d793a000 r--p 00014000 08:07 35355                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb5d793a000-7fb5d793b000 rw-p 00015000 08:07 35355                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb5d793b000-7fb5d7a23000 r-xp 00000000 08:07 1011991                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7fb5d7a23000-7fb5d7c22000 ---p 000e8000 08:07 1011991                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7fb5d7c22000-7fb5d7c2a000 r--p 000e7000 08:07 1011991                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7fb5d7c2a000-7fb5d7c2c000 rw-p 000ef000 08:07 1011991                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.14
7fb5d7c2c000-7fb5d7c41000 rw-p 00000000 00:00 0 
7fb5d7c41000-7fb5d7c4d000 r-xp 00000000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7fb5d7c4d000-7fb5d7e4c000 ---p 0000c000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7fb5d7e4c000-7fb5d7e4d000 r--p 0000b000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7fb5d7e4d000-7fb5d7e4e000 rw-p 0000c000 08:07 378536                     /usr/local/lib/enchant/libenchant_ispell.so
7fb5d7e4e000-7fb5d7e90000 r-xp 00000000 08:07 183097                     /usr/lib/libibus.so.2.0.0
7fb5d7e90000-7fb5d8090000 ---p 00042000 08:07 183097                     /usr/lib/libibus.so.2.0.0
7fb5d8090000-7fb5d8091000 r--p 00042000 08:07 183097                     /usr/lib/libibus.so.2.0.0
7fb5d8091000-7fb5d8092000 rw-p 00043000 08:07 183097                     /usr/lib/libibus.so.2.0.0
7fb5d8092000-7fb5d8093000 rw-p 00000000 00:00 0 
7fb5d8093000-7fb5d8098000 r-xp 00000000 08:07 213280                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7fb5d8098000-7fb5d8297000 ---p 00005000 08:07 213280                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7fb5d8297000-7fb5d8298000 r--p 00004000 08:07 213280                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7fb5d8298000-7fb5d8299000 rw-p 00005000 08:07 213280                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7fb5d8299000-7fb5d829b000 r-xp 00000000 08:07 278466                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7fb5d829b000-7fb5d849a000 ---p 00002000 08:07 278466                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7fb5d849a000-7fb5d849b000 r--p 00001000 08:07 278466                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7fb5d849b000-7fb5d849c000 rw-p 00002000 08:07 278466                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7fb5d849c000-7fb5d849e000 r-xp 00000000 08:07 35405                      /lib/x86_64-linux-gnu/libutil-2.13.so
7fb5d849e000-7fb5d869d000 ---p 00002000 08:07 35405                      /lib/x86_64-linux-gnu/libutil-2.13.so
7fb5d869d000-7fb5d869e000 r--p 00001000 08:07 35405                      /lib/x86_64-linux-gnu/libutil-2.13.so
7fb5d869e000-7fb5d869f000 rw-p 00002000 08:07 35405                      /lib/x86_64-linux-gnu/libutil-2.13.so
7fb5d869f000-7fb5d86ac000 r-xp 00000000 08:07 35404                      /lib/x86_64-linux-gnu/libudev.so.0.11.1
7fb5d86ac000-7fb5d88ab000 ---p 0000d000 08:07 35404                      /lib/x86_64-linux-gnu/libudev.so.0.11.1
7fb5d88ab000-7fb5d88ac000 r--p 0000c000 08:07 35404                      /lib/x86_64-linux-gnu/libudev.so.0.11.1
7fb5d88ac000-7fb5d88ad000 rw-p 0000d000 08:07 35404                      /lib/x86_64-linux-gnu/libudev.so.0.11.1
7fb5d88ad000-7fb5d88c4000 r-xp 00000000 08:07 792146                     /usr/lib/libgvfscommon.so.0.0.0
7fb5d88c4000-7fb5d8ac3000 ---p 00017000 08:07 792146                     /usr/lib/libgvfscommon.so.0.0.0
7fb5d8ac3000-7fb5d8ac4000 r--p 00016000 08:07 792146                     /usr/lib/libgvfscommon.so.0.0.0
7fb5d8ac4000-7fb5d8ac5000 rw-p 00017000 08:07 792146                     /usr/lib/libgvfscommon.so.0.0.0Aborted

```Any suggestions what i can do to fix that?

---

### Post by mado89 on 2011-09-11
I tried removing libenchant1c2a and reinstallling it
also removing myspell and reinstalling it.
But i still have the same issue :(

---

