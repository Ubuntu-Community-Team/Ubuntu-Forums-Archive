---
title: "Did I use the right download for 18.x for use on Raspberry Pi ?"
date: 2022-08-05
forum: Installation &amp; Upgrades
---

### Post by southof40 on 2022-08-05
I have a Raspberry Pi 4 I want to install Ubuntu 18.x onto . 

The links on the Ubuntu website and the links within Raspberry Pi Imager don't go any further back than 20.x so instead I downloaded "ubuntu-18.04.6-desktop-amd64.iso" from [https://releases.ubuntu.com/18.04/?C=S;O=A](https://releases.ubuntu.com/18.04/?C=S;O=A) and used the "other" option within the Imager to make the boot disk.

When I use the resulting boot disk that I get a blank screen. The screen in question is not a HDMI screen, I am accessing it through via a protocol convertor to a VGA port on the monitor. I read in [this question]("https://askubuntu.com/a/1369010") that with an non-HDMI screen I might need to edit /boot/firmware/usercfg.tx to include ...

```

hdmi_safe=1
hdmi_force_hotplug=1

```

... so I created that file (the 'firmware' directory didn't exist so I created that too) and put that content into it but when I try to boot again I get the same response.

When I switch boot cards so that the one supplied with the Pi, with the Raspian OS, is used the system boots normally.

Did I choose the wrong file to make the boot disk from ? 

Thanks

---

### Post by mikewhatever on 2022-08-05
No. AMD64 is for Intel/AMD architecture, won't work on RP.  Also, I doubt 18.04.x has support for RP4. Get 20.04 or 22.04 instead from the right page.

---

