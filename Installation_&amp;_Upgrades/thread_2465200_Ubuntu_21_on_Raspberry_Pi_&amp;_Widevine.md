---
title: "Ubuntu 21 on Raspberry Pi &amp; Widevine"
date: 2021-07-25
forum: Installation &amp; Upgrades
---

### Post by ottawahacker on 2021-07-25
Has anyone figured out how to get Widevine or DRMs working on raspberry pi? I noticed that Raspberry pi os has now an official package for libwidevine but was wondering if Ubuntu will have one soon?

Thanks

---

### Post by MAFoElffen on 2021-07-25
I have Ubuntu 20.04 LTS Desktop running on my Pi4... I notice that the SnapCraft Store has libwidevine as a snap. In this link they made it work for Netflix... btu some other things still don't work... [https://forum.snapcraft.io/t/chromium-libwidevine-and-other-drm/10896/5](https://forum.snapcraft.io/t/chromium-libwidevine-and-other-drm/10896/5)

One of the challenges there, is that Google Chrome does not have a version for Pi or Arm. But there is the OpenSource version of Chromium available. But I think they somehow made it work there for Firefox... 

I don't know how, because I can only get limited video in Firefox on my Pi4. But I haven't really looked into that much, as playing video's on mine is not really a priority (yet). I have heard from my son, who does Pi and talked me into mine, is that Video playback is really slow, because of it's onboard framebuffer. So I haven't really expected much on that. He did tell me that it work's better on Ubuntu Mate...

---

### Post by ottawahacker on 2021-07-29
> **MAFoElffen said:**
> I have Ubuntu 20.04 LTS Desktop running on my Pi4... I notice that the SnapCraft Store has libwidevine as a snap. In this link they made it work for Netflix... btu some other things still don't work... [https://forum.snapcraft.io/t/chromium-libwidevine-and-other-drm/10896/5](https://forum.snapcraft.io/t/chromium-libwidevine-and-other-drm/10896/5)


Ok so after countless installs and forum reads... Widevine only works on 32 bit and has never been made available for 64 bit so that eliminates any possibility with the new desktop version because it is only available in 64 bit.
I tried installing server 20.04 LTS and upgrade to desktop but that is really messy and there are many features that end up broken (like wifi).

Widevine is a piece of cake with Raspberry Pi os 32 bit - there is an apt package to install and voila, widevine shows up in the chromium plugins.

Also I noticed that most of the hardware video decoding and opengl doesn't seem to work in the current desktop 21.

---

### Post by MAFoElffen on 2021-07-29
For me on 20.04, to deal with the missing codecs, because codecs are non-free, I installed ffmpeg and ubuntu-restricted-extras... Those two packages took care of the majority of codecs. You are going to find that on any Linux Distro, because of them being 3rd Party non-free.

The others, well, I'm still working on myself. such as native MPEG-4 + ASP support in browsers... I haven't found any clean way for that yet on Pi4...

For OpenGL, I happen to know that OpenGL works on mine. I just happen to be running and testing Nested Virtuals and VirGL in KVM on this Pi4, Some things work so far, some things are close. But I'm doing a lot more than just basic OpenGL on the host. To confirrm to you that OpenGL is working...
```
mafoelffen@ubuntu:~$ glxinfo | grep '^direct rendering:'
direct rendering: Yes

mafoelffen@ubuntu:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 3.1 Mesa 20.2.6

```
I can admit, that I don't fully understand how it does it, as there is nothing "special" about the video hardware on this board. I mean, it's just an onbaord frame-buffer. LOL

---

### Post by ottawahacker on 2021-07-29
> **MAFoElffen said:**
> The others, well, I'm still working on myself. such as native MP4 + ASP in browsers... I haven't found any clean way for that yet on Pi4...

Raspberry OS has a special plugin to enable h264 from youtube and I believe it is all hardware accellerated.

---

### Post by MAFoElffen on 2021-07-29
Just adding the ffmeg apckage to the OS takes care of all forms of H264...
```
sudo apt install ffmeg
```
You can test that on these 3 HTML Pages:
  - [http://demo.nimius.net/video_test/](http://demo.nimius.net/video_test/)
  - [https://html5test.com/](https://html5test.com/)
  - [http://camendesign.com/code/video_for_everybody/test_yt.html](http://camendesign.com/code/video_for_everybody/test_yt.html)

On the second link... Most of those work just by adding that 1 package, except Mpeg4... That is how it's been since, I think Ubuntu Desktop version 12.04(?) on any platform.

EDIT... OpenGL comes from the version of your Mesa Driver... Look at the edit of my last post.

---

### Post by ActionParsnip on 2021-07-31
I used a docker image which had the required DRM gubbins. Works perfectly.
[https://www.linuxadictos.com/en/how-to-view-drm-protected-content-on-raspberry-pi-vol-2.html](https://www.linuxadictos.com/en/how-to-view-drm-protected-content-on-raspberry-pi-vol-2.html)

---

