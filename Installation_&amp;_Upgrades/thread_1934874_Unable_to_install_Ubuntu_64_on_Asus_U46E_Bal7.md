---
title: "Unable to install Ubuntu 64 on Asus U46E Bal7"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by vra5107 on 2012-03-03
Hi

          I have been trying to install ubuntu 11.10 64 on my new laptop. The installation goes fine but the OS never boots up. So far I have gone through quite a few options.


[LIST]
[*]Add acpi=off boot option
[*]Add noapic boot option
[*]Add nolapic boot option
[*]Edit Grub to include quiet splash nomodeset.
[*]Edit grub to include acpi_osi="Linux"
[/LIST]


OS boots up very inconsistently, so I am unable to find a repeatable solution. Each of the above options works once and then on reboot everything goes wrong. I can't restart it again for a while.


Here are the last few lines I see.


[PHP]
[0.303961] ... version:                               3
[0.303993] ... bit width:                            48
[0.304026] ... generic registers:               4
[0.304058] ... value mask:                       0000ffffffffffff
[0.304093] ... max period:                       000000007fffffff
[0.304128] ... fixed-purpose events:       3
[0.304160] ... event mask:                      000000070000000f
[0.304519] ... Booting Node    0, Processors     #1
[0.423851]      #2
[0.531725]      #3

[/PHP]


Thats it, it just stays there. I have spent quite a bit of time on this. Any help is appreciated. Also, if you can think of an alternative OS that I can get up and running please let me know. I could always try but I have done way too may installations already. Listed below are the ones I have tried.



Ubuntu 11.10 Desktop 32Bit ( Only 4 gb of memory out of the 8GB, but it works great )
Ubuntu 11.10 Desktop 64Bit ( Doesn't boot )
Ubuntu 11.10 Server 64 Bit ( Fails to boot  )
Ubuntu 12.04 Beta 1 Desktop 64Bit ( Fails to boot ) 





Sincere thanks
Venkat

---

### Post by vra5107 on 2012-03-03
I was able to install server first and KDE desktop over it. So, I have the computer up, but for some reason it doesn't detect laptop monitor. It does detect the secondary monitor though.

Venkat

---

### Post by vra5107 on 2012-03-03
HI


I have looked at the page below and learned a little bit about asking hardware problems. So, I will try to give a little bit more information.

[http://askubuntu.com/questions/14008/i-have-a-hardware-detection-problem-what-logs-do-i-need-to-look-into](http://askubuntu.com/questions/14008/i-have-a-hardware-detection-problem-what-logs-do-i-need-to-look-into)



[LIST]
[*]Xorg.0.log attached to the post.
[*]LIBGL_DEBUG=verbose glxinfo  (  look at attachment glxinfo.txt )
[*]lspci -nn | grep VGA
[LIST]
[*]```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
```
[/LIST]
[*]I have added this grub entry to get it running. ```
GRUB_CMDLINE_LINUX="noapic nomodeset"
```.
[/LIST]


Let me know if there is anything missing here. Please help me on this. 


Sincerely
Venkat

---

### Post by vra5107 on 2012-03-04
[bugs.launchpad.net/ubuntu/+source/linux/+bug/912397]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397")

The fix lies dormant beneath the bug.

[http://askubuntu.com/questions/109846/screen-resolution-and-multiple-monitors-kubuntu-11-10-asus-u46e-bal7](http://askubuntu.com/questions/109846/screen-resolution-and-multiple-monitors-kubuntu-11-10-asus-u46e-bal7)

---

### Post by skaag on 2012-04-26
Did you manage to resolve this?
Having the very same experience myself on the same laptop.

---

