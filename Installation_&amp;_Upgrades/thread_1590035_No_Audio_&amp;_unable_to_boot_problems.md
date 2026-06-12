---
title: "No Audio &amp; unable to boot problems"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2010-10-07
Just thought I'd post up how I fixed the only 2 errors I came across when upgrading from Lucid to Maverick Beta (yesterday):
[LIST=1]
[*]Couldn't boot - I'm using grub 0.97 (because I use fakeraid and grub2 doesn't support that yet) and when I upgraded I could no longer boot using the default grub entry. I had to remove the two entries for the older kernel from my menu.lst file and then I could boot.
[*]No Audio - I had no audio after the upgrade. Running "ubuntu-bug audio" told me that pulseaudio had crashed. I ran "rm -rf ~/.pulse*" and rebooted and audio worked again.
[/LIST]

Everything else in the update went according to plan, but do keep a close eye on any diff's that it presents cause you may want to overwrite and then manually re-apply the custom settings.

---

