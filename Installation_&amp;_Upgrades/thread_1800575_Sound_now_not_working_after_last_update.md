---
title: "Sound now not working after last update"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by mattmank on 2011-07-09
Hi All,
I have been using Ubuntu for a few years now and have managed to solve any problems through this great forum.
I am now a bit lost as to what to do with this latest issue. I upgraded my desktop machine yesterday and now the sound has stopped working. This was the upgrade:
Start-Date: 2011-07-08  14:42:21
Upgrade: nvidia-current:i386 (270.41.19-0ubuntu1~xup~natty, 275.09.07-0ubuntu1~natty~xup1), bind9-host:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), libcupscgi1:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), dnsutils:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), libdecoration0:i386 (0.9.4+bzr20110606-0ubuntu1~natty1, 0.9.4+bzr20110606-0ubuntu1~natty2), cups-client:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), apt-transport-https:i386 (0.8.13.2ubuntu3, 0.8.13.2ubuntu4), libcupsmime1:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), libdns69:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), initramfs-tools-bin:i386 (0.98.8ubuntu3, 0.98.8ubuntu3.1), libgpod4:i386 (0.8.0-2, 0.8.0-2ubuntu0.1), banshee:i386 (2.0.0-2ubuntu1, 2.0.0-2ubuntu2), libisccc60:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), cups-ppdc:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), banshee-extension-soundmenu:i386 (2.0.0-2ubuntu1, 2.0.0-2ubuntu2), apt-utils:i386 (0.8.13.2ubuntu3, 0.8.13.2ubuntu4), initramfs-tools:i386 (0.98.8ubuntu3, 0.98.8ubuntu3.1), compiz-plugins:i386 (0.9.4+bzr20110606-0ubuntu1~natty1, 0.9.4+bzr20110606-0ubuntu1~natty2), libcupsppdc1:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), apt:i386 (0.8.13.2ubuntu3, 0.8.13.2ubuntu4), cups-common:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), liblwres60:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), libcups2:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), libbind9-60:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), cups:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), libcupsdriver1:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), banshee-extension-ubuntuonemusicstore:i386 (2.0.0-2ubuntu1, 2.0.0-2ubuntu2), libgpod-common:i386 (0.8.0-2, 0.8.0-2ubuntu0.1), cups-bsd:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), libisccfg62:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), libcupsimage2:i386 (1.4.6-5ubuntu1.2, 1.4.6-5ubuntu1.3), libva1:i386 (1.0.8-3, 1.0.12-1~xup), compiz:i386 (0.9.4+bzr20110606-0ubuntu1~natty1, 0.9.4+bzr20110606-0ubuntu1~natty2), libisc62:i386 (9.7.3.dfsg-1ubuntu2.1, 9.7.3.dfsg-1ubuntu2.2), compiz-core:i386 (0.9.4+bzr20110606-0ubuntu1~natty1, 0.9.4+bzr20110606-0ubuntu1~natty2), compiz-gnome:i386 (0.9.4+bzr20110606-0ubuntu1~natty1, 0.9.4+bzr20110606-0ubuntu1~natty2)
End-Date: 2011-07-08  14:44:17
Machine is a bit of a home brew with on-board sound and SB ca106 sound card.
Can anyone give me a direction to go, where to look for information and what to do. If more information is required then I can provide it, just let me know what.
Regards,
Matt

---

### Post by mattmank on 2011-07-09
OK, I've just run speaker-test with the following result:
speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 10.959892
 0 - Front Left
Time per period = 5.095539
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

Tried this before and it just kept trying front left with no result, no sound.

---

### Post by mörgæs on 2011-07-09
Hi, welcome to the fora.

I guess posting here will give you better results:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

