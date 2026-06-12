---
title: "NO AUDIO in my Sony Vaio VPCEB34EN"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by rajkumar.neelam on 2011-07-24
[SIZE=3]hi..
i have installed Ubuntu 10.04 in my Sony Vaio laptop VPCEB34EN.
when i am playing any movie or song it is playing but not able to hear sound. when i am watching video in youtube, able to hear very less sound.

please help[/SIZE]

---

### Post by tuxnani on 2011-07-25
You should check whether the required sound libraries, ie gstreamer libraries have been installed or not.
Installing vlc could have enabled the video drivers, but not the audio drivers.
Being able to listen to videos at youtube simply means you have to increase volume at alsamixer.
just go to terminal and type alsamixer and increase the volume accordingly.

---

