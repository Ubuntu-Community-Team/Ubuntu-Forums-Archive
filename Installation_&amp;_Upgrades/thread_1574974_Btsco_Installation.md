---
title: "Btsco Installation"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by harsha1987 on 2010-09-15
Hi,

I am having problem installing kernel module for btsco.
I downloaded the latest version of btsco that is btsco-0.5, following is the problem that I encountered while installing,

make[1]: Entering directory `/usr/src/linux-headers-2.6.28-19-generic'
  CC [M]  /home/ic011034/btsco-0.5/kernel/btsco.o
In file included from /home/ic011034/btsco-0.5/kernel/btsco.c:46:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/ic011034/btsco-0.5/kernel/btsco.c: In function ‘snd_card_bt_sco_playback_close’:
/home/ic011034/btsco-0.5/kernel/btsco.c:444: error: implicit declaration of function ‘snd_assert’
/home/ic011034/btsco-0.5/kernel/btsco.c:444: error: expected expression before ‘;’ token
/home/ic011034/btsco-0.5/kernel/btsco.c: In function ‘snd_card_bt_sco_capture_close’:
/home/ic011034/btsco-0.5/kernel/btsco.c:468: error: expected expression before ‘;’ token
/home/ic011034/btsco-0.5/kernel/btsco.c: In function ‘snd_card_bt_sco_new_mixer’:
/home/ic011034/btsco-0.5/kernel/btsco.c:677: error: expected expression before ‘return’
/home/ic011034/btsco-0.5/kernel/btsco.c: In function ‘snd_card_bt_ioctl’:
/home/ic011034/btsco-0.5/kernel/btsco.c:716: error: implicit declaration of function ‘kill_proc’
/home/ic011034/btsco-0.5/kernel/btsco.c:718: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long int’
/home/ic011034/btsco-0.5/kernel/btsco.c: In function ‘snd_card_bt_sco_thread’:
/home/ic011034/btsco-0.5/kernel/btsco.c:909: error: implicit declaration of function ‘try_to_freeze’
/home/ic011034/btsco-0.5/kernel/btsco.c:1110: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long int’
/home/ic011034/btsco-0.5/kernel/btsco.c: In function ‘snd_card_bt_private_free’:
/home/ic011034/btsco-0.5/kernel/btsco.c:1136: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long int’
make[2]: *** [/home/ic011034/btsco-0.5/kernel/btsco.o] Error 1
make[1]: *** [_module_/home/ic011034/btsco-0.5/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-19-generic'
make: *** [default] Error 2

I don't know what these errors mean, could anyone help me on this issue??

Thanks in advance.

With Best Regards,
Harsha

---

### Post by lechien73 on 2010-09-15
According to the SourceForge support page for btsco, the project has been dormant since 2006 and doesn't support the newer kernels.

If you were wanting btsco for Bluetooth audio or a headset, then check these recently-updated community pages for instructions:

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)
[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

