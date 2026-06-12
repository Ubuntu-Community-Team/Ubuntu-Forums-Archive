---
title: "Boot-repair screen blinking display problem"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by steph6 on 2016-01-11
Hi everybody, glad to join the community.

I got an HP proliant G4 350 ML. I've installed last ubuntu desktop TLS release, the 14.04.3 from a live usb.

Installation is OK, but when I restart the server, I got the message error: file '/grub/i386-pc/normal.mod' not found

So I've done some searches on the net and I've decided to use boot-repair.

But when I start the server on boot-repair usb, I got a terminal menu asking for starting boot-repair or boot-repair (fail safe). No matter of which option I choose, my screen start flashing. It displays the boot-repair screen (with somebody jumping) but :
  - it's allmost green
  - there is too a blank square in the center of the screen, I supposed that it's the boot-repair GUI box
  - it display during only about 1 second
and then the screen turn again black about 1 second and it displays again the green picture about 1 second, and it still go round as this severals minutes before staying definitely black

I don't have founded any information about this kind of bug. Does somebody got an idea ? Thanks a lot for your help.

---

### Post by grahammechanical on 2016-01-11
> when I start the server

Server? Is this a server machine? What graphic adapter does it have?

Server machines run server versions of the operating systems which do not have a graphical desktop environment. Therefore, a server machine may not have a graphic adapter powerful enough to run a live session with a graphical user interface.

Regards.

---

### Post by steph6 on 2016-01-11
Hi. thanks for reply.

It got an Integrated ATI RAGE XL Video Controller with 8-MB SDRAM Video MemoryVGA connector; up to 1200 x 1600 resolution supported.

It ran well the ubuntu desktop 14.04.3 from a live usb.

---

### Post by oldfred on 2016-01-11
I do not know AMD, but both nVidia & AMD typically need nomodeset to boot until proprietary driver is installed.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This was in release notes, not sure if fixed yet as I do not have AMD.

 With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel

---

