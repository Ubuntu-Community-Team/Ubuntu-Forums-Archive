---
title: "sound card problem"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by mirkash on 2006-08-21
after upgrading to dapper my sound card aint working anymore
I have AC97 integrated on asus a7v133 (and it works under Xp installed - dual system boot)
now here are some indicators

mirkash@ubuntu:/$ cat /proc/asound/cards
--- no soundcards ---
lsmod gave following results
[http://paste.ubuntu-nl.org/21353](http://paste.ubuntu-nl.org/21353)

mirkash@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] PCI Bridge
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


xorg.log:

[http://paste.ubuntu-nl.org/21355](http://paste.ubuntu-nl.org/21355)

please help
Thanks

---

