---
title: "Lost internal microphone after I updated to 22.04"
date: 2022-10-10
forum: Installation &amp; Upgrades
---

### Post by loic-quertenmont on 2022-10-10
Hello,

I've just upgraded my system to ubuntu 22.04 through apt dist-upgrade,
but I've lost the internal sound/microphone device support on my Lenovo Thinkpad P15 Gen2 laptop.

I was able to restore the sound device by adding the following line at the end of  /etc/modprobe.d/alsa-base.conf :
```
options snd-hda-intel dmic_detect=0

```

But this didn't restore the internal microphone, which is not detected at all.
I've tried adding the following line into the same file
```
options snd-hda-intel model=lenovo

```
But it didn't help.
I've also tried with model=thinkpad or [COLOR=#333333][FONT=Ubuntu]laptop-amic  or [/FONT][/COLOR][FONT=Ubuntu, Tahoma, Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]laptop-dmic [/COLOR][/FONT]
[FONT=Ubuntu, Tahoma, Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]but none of these help either.[/COLOR][/FONT]

[FONT=Ubuntu, Tahoma, Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]I'd appreciate any help or suggestion to solve the issue,[/COLOR][/FONT]
[FONT=Ubuntu, Tahoma, Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]Thanks in advance[/COLOR][/FONT]
[FONT=Ubuntu, Tahoma, Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#333333]Loic[/COLOR][/FONT]

---

### Post by QIII on 2022-10-10
Hello!

dist-upgrade does not upgrade your release version.  It upgrades all the packages previously identified by the update process most recently run..

What release were you using before?  Are you sure you are on 22.04 now?

Would you please post the results of 

```
lsb_release -a
```

just as a quick check?

---

### Post by loic-quertenmont on 2022-10-10
I was on 20.04

lsb_release -a
LSB Version:	core-11.1.0ubuntu4-noarch:printing-11.1.0ubuntu4-noarch:security-11.1.0ubuntu4-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy

---

### Post by loic-quertenmont on 2022-10-11
any help please...

---

### Post by loic-quertenmont on 2022-10-11
I believe this thread is related to my issue, but it's a complete mess ;-)
[https://bugzilla.kernel.org/show_bug.cgi?id=208555](https://bugzilla.kernel.org/show_bug.cgi?id=208555)
My device is a ALC287 for sure.

---

### Post by loic-quertenmont on 2022-10-11
I've finally got it working
I followed this thread on Lenovo support: [https://forums.lenovo.com/t5/Ubuntu/ThinkPad-X1-Carbon-7th-Gen-X1C7-mirophone-not-working/m-p/4484156?page=3](https://forums.lenovo.com/t5/Ubuntu/ThinkPad-X1-Carbon-7th-Gen-X1C7-mirophone-not-working/m-p/4484156?page=3)
Which lead me to the solution that is here: [https://mathieularose.com/ubuntu-19-10-on-lenovo-thinkpad-x1-carbon-7th-gen](https://mathieularose.com/ubuntu-19-10-on-lenovo-thinkpad-x1-carbon-7th-gen)

---

### Post by jussi-pokko on 2023-01-24
I had the same problem with my Thinkpad P14s after release upgrade to 22.04. Fixed by installing alsa-ucm-conf package and restarting pulseaudio.

---

