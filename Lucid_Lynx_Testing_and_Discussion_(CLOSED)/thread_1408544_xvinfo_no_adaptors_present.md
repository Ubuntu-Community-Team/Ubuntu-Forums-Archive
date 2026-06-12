---
title: "xvinfo: no adaptors present"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by code850 on 2010-02-16
In karmic I had xv working when I disabled kernel mode setting. Now I have lucid where everything is working nice except xv. Disabling kernel mode setting here crashes the system during boot. Any ideas as how to solve this? I'm not sure whether this is specific to my graphics card intel 855gm or not.

---

### Post by Ibidem on 2010-02-16
xv works fine here:

```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Textured Video"
    number of ports: 16
    port base: 69
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 3
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SYNC_TO_VBLANK" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 5
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x434d5658 (XVMC)
        guid: 58564d43-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
```

That's i945 graphics, default on kms when plymouth isn't installed... (on or off? I haven't figured out)

---

### Post by psyke83 on 2010-02-16
> **code850 said:**
> In karmic I had xv working when I disabled kernel mode setting. Now I have lucid where everything is working nice except xv. Disabling kernel mode setting here crashes the system during boot. Any ideas as how to solve this? I'm not sure whether this is specific to my graphics card intel 855gm or not.

Xv overlay is not supported with Intel 855GM when KMS is active (though I think support is present/will be present in kernel 2.6.33).

Since my laptop which uses 855GM has recently died I can't test for you, but my suspicions are either a) Plymouth is causing the crash, or b) UMS (user-mode setting) has now been removed from the Intel driver.

Just in case it's Plymouth, try booting *without* "quiet splash" and *with* "nomodeset". You may also want to purge the plymouth package from your system.

---

### Post by code850 on 2010-02-17
I purged plymouth and disabled kernel mode setting as well as removing quiet and splash from grub. Rebooted the system and it crashed just before starting gdm. Everything was locked and nothing resopnsive. I'm thinking of trying kernel 2.6.33, any idea where to get it from?

---

### Post by psyke83 on 2010-02-17
All the information you need is in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/395932"), and you can find the latest unofficial kernel build [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc8/").

---

### Post by code850 on 2010-02-17
Solved by upgrading the kernel to 2.6.33 as well as upgrading Xorg from edgers. Kernel upgrade alone was not sufficient, so the problem was probably caused by intel driver.

---

