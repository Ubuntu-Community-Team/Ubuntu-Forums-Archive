---
title: "Can't install Ubuntu - Ryzen 5 bug?"
date: 2018-05-14
forum: Installation &amp; Upgrades
---

### Post by 006.9 on 2018-05-14
Hi guys I'm having problems installing Ubuntu on my new PC build and I'm wondering if someone can point me in the right direction? I bought the following parts and put them in a case:

Asus B350M-A
Ryzen 5 2400g
2x4gb Corsair vengeance ddr4 3200
Toshiba X300 4tb HDD

I installed KDE Neon from USB but it seemed a bit slow and I got some errors when trying to install programs so I decided to format and start again. I had problems formatting, gparted said[I] [I]'partitions have been written, but we have been unable to inform the kernel of the change' 

[/I][/I]I put it in my old PC to format it, also had to reset the MB cmos battery as the signal to monitor had been lost so at this point everything is 100% reset. I used the Asus EZ Flasher to flash my MB with the latest bios to make sure I was both up to date + back to normal, as I changed a number of settings before the 1st install.

The problem is - from that point on I've been unable to boot any Ubuntu live install - I've tried Neon, Kubuntu + Ubuntu and the same happens every time - the live USB starts to load, gives this error:[I][I]

[IMG]https://image.ibb.co/igiT3y/Capture.png[/IMG]


From there, Neon fails and gives a blank page asking for logon + password and Kubuntu+Ubuntu live CD's give the above message then split screens like this:

[IMG]https://image.ibb.co/ixrWOy/1.jpg[/IMG]

So now I'm quite stuck, this is my first Ubuntu install - I'm moving over after years of win7 so this is new to me and problem solving is difficult. I noticed other people with a similar problem [https://bugzilla.redhat.com/show_bug.cgi?id=1549939](https://bugzilla.redhat.com/show_bug.cgi?id=1549939) and I'm unsure as to whether this is a Ryzen bug or something I've done/not done.

Any help would be much appreciated[/I][/I]

---

### Post by experimancer on 2018-05-27
You need to use kernel 4.17 and MESA 18.2 to run any Linux distro in AMD Ryzen5 2400G. There is no other way to get full graphics modes and acceleration from those Raven Ridge APUs in Linux.

---

### Post by amvitty on 2018-05-27
Review this:
[https://www.servethehome.com/amd-ryz...stant-crashes/]("https://www.servethehome.com/amd-ryzen-with-ubuntu-here-is-what-you-have-to-do-to-fix-constant-crashes/")
and
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1671360]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1671360")
and I think it uses UEFI?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

