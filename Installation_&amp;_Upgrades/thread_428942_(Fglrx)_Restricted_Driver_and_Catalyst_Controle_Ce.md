---
title: "(Fglrx) Restricted Driver and Catalyst Controle Center"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by superyounan1 on 2007-04-30
I recently installed the ATI driver fglrx through Feisty's restricted-driver app and followed a guide to install XGL and get beryl going - very nice!

I noticed that the driver that was installed however isnt the latest version, and it doesnt include the new AMD Catalyst Control Center for Linux. 

Should i download the 8.36.5 automatic installer to get up to date? I heard about some compatibility issues, but I dont know if they apply...

What i really want is an easy way to configure my TV-out options. I'm assuming what I'm looking for is 'dual head' and overlay support, which I can manually configure now with the 'aticonfig' utility, but I feel like I'm shooting in the dark with that.

---

### Post by qamelian on 2007-04-30
It depends on what card you've got. ATI has dropped support for a number of cards in the last several driver releases. The last release to support my card was around 8.28.:(

---

### Post by superyounan1 on 2007-04-30
I have the ATI 9800 All-in-wonder, i think its still supported. Heres what the AMD site says when you look at the list of previous driver versions:

> 
8.28.8

August 18, 2006

Note - This is the last driver version to support the following products
Radeon® 8500/9000/9100/9200/9250
Mobility™ Radeon® 9000/9100/9200
Radeon® IGP 9000/9100/9200


Looks like i barely squeaked by...

---

### Post by qamelian on 2007-04-30
Yeah, but that's what I meant. The newest drivers aren't usable on a number of cards supported by 8.28.  Not that it's a big deal to me, I guess. The open source drivers always gave me better performance than the native drivers any way. I'm using them with a Mobility Radeon 9000 IGP and they work great. Compiz and Beryl work great without messing about with FGLRX and XGL. On my card anyway.

---

### Post by superyounan1 on 2007-04-30
I was happy with the open-source driver too, but it has some big problems.

1. TV-out was horrible, the best I could get was a seizure inducing flickering screen
2. I always had to disable desktop effects to watch any video files, for example with VLC, the file would play and I'd hear the audio, but the screen was black.. i had to "flick" the window to get it to display video, and it would just cut out again, no fullscreen ever worked.

With fglrx drivers, TV-out works well and video is flawless, desktop looks nice with XGL, etc.


If you have any advice about upgrading to the latest ATI drivers with Feisty, please let me know

---

### Post by qamelian on 2007-04-30
> **superyounan1 said:**
> I was happy with the open-source driver too, but it has some big problems.

1. TV-out was horrible, the best I could get was a seizure inducing flickering screen
2. I always had to disable desktop effects to watch any video files, for example with VLC, the file would play and I'd hear the audio, but the screen was black.. i had to "flick" the window to get it to display video, and it would just cut out again, no fullscreen ever worked.

With fglrx drivers, TV-out works well and video is flawless, desktop looks nice with XGL, etc.


If you have any advice about upgrading to the latest ATI drivers with Feisty, please let me know
As for number 2 above, you just need to change one setting in GStreamer to make video work. I gave up on the ATI drivers a long time ago, so I'm afraid I won't be much help.

---

### Post by superyounan1 on 2007-05-01
I'm thinking im just going to gamble and go for it tomorrow, if someone can chime in, please do so

---

