---
title: "Ubuntu 12.10 (and Fedora 17) x64 on Compaq Presario CQ56 boot fail"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by Bernicc on 2012-10-28
Hello,

I become desperate. I can't start many Linux distributions round about kernel greater 3.4.x.

Currently there run a Fedora 16 x64 system (3.4.11). An upgrade (preupgrade) to Fedora 17 (Linux 3.3.4) Fail (black screen), a directly installation fail (black screen). And now I try Ubuntu 12.10 and I'll get a black screen although.

But there is a little hope, I'll get something in the console with parameters:
xforcevesa acpi=off nomodeset

I'll have make two videos, first with Ubuntu, second with Fedora 17, of course anybody has a great idea?

[http://youtu.be/rbsnP8E_qek](http://youtu.be/rbsnP8E_qek)
[http://youtu.be/uMM95DsYA1Q](http://youtu.be/uMM95DsYA1Q)

I'll try to log in via ssh in my local LAN, but I get a "No route to host" :(

PS: CD/DVD is correct (checked twice), same game on USB Stick.

Thank you for any help!

---

### Post by Bernicc on 2012-11-07
I love netconsole :)

Here are 4 boot logs.

[http://bit.ly/RKcxo4](http://bit.ly/RKcxo4)
[http://bit.ly/SJvEME](http://bit.ly/SJvEME)
[http://bit.ly/S6qXvx](http://bit.ly/S6qXvx)
[http://bit.ly/UA0uqL](http://bit.ly/UA0uqL)

---

### Post by oldfred on 2012-11-07
Intel video is supposed to just work. Not sure if any of this applies you your version of Intel or what other boot parameters may be required.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

For Intel 945g info to show the graphic card properly,install mesa-utils package from USC.

---

