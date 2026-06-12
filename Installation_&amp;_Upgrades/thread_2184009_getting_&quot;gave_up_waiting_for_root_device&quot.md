---
title: "getting &quot;gave up waiting for root device&quot;"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by bzupnick on 2013-10-27
I get the GRUB menu, hit 'ubuntu', and then it cuts to a black screen with a blinking cursor. After ~a minute, it gives this message:

```
[COLOR=#000000][FONT=arial]Gave up waiting for root device. Commone Porlbmes:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]    - boot args (cat /proc/cmdline)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]        - check rootdelay= (did the system wait long enough?)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]        - check root= (did the system wait for the right device?)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]    - missing modules (cat /proc/modules; ls /dev)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]ALERT! /dev/disk/by-uuid/7987ff8c-9aa4-4e36-8b43-32d4ac1aa623 does not exist[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]dropping to shell!
[/FONT][/COLOR]

```[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]and it shows a BusyBox command prompt.

My Lenovo T530 has a 16gb SSD, where Ubuntu was installed, and a 500gb HDD, and a [COLOR=#666666][FONT=Verdana]NVIDIA NVS 5400M Graphics with Optimus Technology, 1GB DDR3 Memory [/FONT][/COLOR]Graphics card.

I installed both the OS and GRUB on the SSD.[/FONT][/COLOR]

---

