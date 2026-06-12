---
title: "Hard locks at login screen"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by archmichael on 2006-07-20
I'm still having problems with this, but I'm determined to make this work.

The installation hard locks at the login screen.

I have an AMD64, but I've tried the 32-bit and 64-bit version. Both the LiveCD and installation hard locks.

I thought it was my ATI Radeon, so I switched videocards with my wife for a GeForce 4 MX and it was still hardlocks. Even with the driver in xorg.conf switched to 'vesa'. 

If I alt-ctrl-f2 as soon as the login screen pops up, I can get a login. When I type 'gdm' I get a "GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL'+failed". If I type 'startx' it says it's locked and I have to delete a file to go forward. After deleting the file 'startx' launches the xsession. The sessions occasionally still hard locks.

Any guidance as to what I should try next?

---

### Post by nalmeth on 2006-07-21
You could try the alternate install disc instead, which probably would be best.

Or if you can't do that right now, try installing ATI's proprietary driver with the live CD via the virtual terminal, if you have an internet connection. 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by archmichael on 2006-07-21
Nalmeth thanks for the reply.

I did manage to use the alternate install to get it install, but it locks up at the login screen.

I now have a nvidia card, because I heard ati cards don't run very well.

I did switch from the amd64 generic kernel to the amd64 k8 kernel.

Now instead of always locking up at the login screen, it only does it sometimes. But eventually it does lock up. It could be a minute or it could be 15 minutes.

I am a noob, but is there some log files I should be looking at? I am looking in /var/log/messages, but I'm not seeing anything there.

---

### Post by nalmeth on 2006-07-21
OK, I would install Nvidia's driver then:
[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation)

Hopefully that fixes the lockups

---

