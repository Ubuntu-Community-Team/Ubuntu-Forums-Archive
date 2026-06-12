---
title: "ECC BIOS crash report + popping sounds &amp; unstable Flash"
date: 2009-10-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roostey on 2009-10-29
I've been running Karmic since the beta release and it's gradually been getting worse with each update, so I decided to do a clean install of the RC, and now I'm getting the following crash report every time I login:

> d64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.

I'm hoping that when this is fixed, it'll also cure the following, which started in the last couple of weeks at about the same time the ECC crash reports began:
[LIST]
[*]30 second Gnome panel hang after login
[*]Shutdown causes a hang 50% of the time
[/LIST]
I hope Canonical make sure this bug is fixed before releasing the final Karmic, it's affecting a lot of people:

[https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/422536?comments=all]("https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/422536?comments=all")

If anyone thinks it's not this bug report that's causing my system to hang, and can suggest a way I can diagnose the problem, then please do.

Other than that, I've also had these problems, which I've been able to resolve:
[LIST][*]An obnoxiously loud popping noise every time audio plays, caused by the audio card being put into sleep mode to conserve power.[/LIST]
Fixed by commenting out the last line of /etc/modprobe.d/alsa-base.conf
"options snd-hda-intel power_save=10 power_save_controller=N"

[LIST][*]Flash crashes about 5 minutes after the browser opens[/LIST]
Flash has never worked reliably on 64bit Ubuntu on any system I've tried it on because of nsplugin. Fix it by removing Ubuntu's flash and nsplugin packages, then install Flash manually.

=======================

If anyone finds this thread, the reason why I was getting the boot and shutdown hang is that something in the changes in the last couple of weeks prior to release broke support for my Sony all-in-one internal card reader. I have disconnected it from the motherboard for now, halving the boot times and stopping any random pauses when the OS tried to query the connected USB devices. The ECC error is unrelated.

---

