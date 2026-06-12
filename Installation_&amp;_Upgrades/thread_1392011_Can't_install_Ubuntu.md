---
title: "Can't install Ubuntu"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by evanshaw on 2010-01-27
Newbie to Ubuntu but an experienced RedHat and SuSE user.
Am unimpressed and yes I know you're bound to take offence to this. 
But I've heard so much about ubuntu that I thought I'd give it a go, yet can't even install it.

I've tried two seperate downloads of the 9.10 installation media with the same results, I can't get to the installer.

Each time I've tried it boots into the livecd portion. So how do I install this thing?

I've even tried from the System/Administration/"Install Ubuntu 9.10" option on the livecd top menu, but get an error: -

"Sorry the program "ubiquity" closed unexpectedly"

there is nothing that explains the installer not running in either dmesg or /var/log/messages. If the livecd can boot, why does the installer not load.

N.B. And I am selecting the "Install Ubuntu" option not the try it without installing option. So can someone please tell me what's going on before I assign it to the bin!

Thank You

---

### Post by snowpine on 2010-01-27
Hi Evan, a few suggestions:

1. Make sure your hardware meets the minimum requirements:

> # 700 MHz x86 processor
# 384 MB of system memory (RAM)
# 8 GB of disk space
# Graphics card capable of 1024x768 resolution
# Sound card
# A network or Internet connection

2. Check the CD for errors (using the provided utility)

3. The [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") is a simple text-based installer that sometimes works where the Live CD installer fails.

---

### Post by evanshaw on 2010-01-28
Thanks snowpine. I'll try the alternative CD.
I'm using VMware Workstation so have met the minimum requirements OK, i.e.: -

2.5 Ghz x86 processor
1024 MB of system memory (RAM)
8 GB of disk space
Graphics card capable of 1024x768 resolution
Sound card
A network or Internet connection

I think the frustrating part was that on chosing the "Install Ubuntu" from the grub menu that it actually managed to go into livecd mode itself, without any logging as to why?

Anyway, thanks for that, I'll give it a shot.

---

### Post by inameiname on 2010-02-09
I tried the Ubiquity regression that Ive heard about in this forum, which is basically  uninstalling the newest version of Ubiquity and putting on the original  version from the Karmic repositories, but it doesn't seem to work  either. Thus, it leads me to believe it's not necessarily Ubiquity as  the main problem because I tried the original Karmic version, 2.0.6, and  it still doesn't work or even open at all.

Is there any other way to install to the hard drive from a Remastersys  Live Cd, without using Ubiquity, the traditional Ubuntu Installer?

---

