---
title: "kickback to login screen"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by balance on 2006-02-20
I recently installed Ubuntu 5.1 from one of the cd's sent to me. The install went fine but now when i login it loads up the desktop and will sit there for a few seconds(the time varies ocasionally) and then the screen flickers goes black and then kicks me back to the login screen. If I repeat this multiple times than it does one of two things:

1. It freezes totally and I have to reboot the computer.
2. It flickers and then comes up with a screen saying that the defaul loader is freezing up. It then attempts to load up the alt. loader which gives me the same options only its in a box with the options at the top in a menu bar. However even when I try logging in from here it still kicks me back to the login screen. 

Right now Im running an HP computer:
Athlon 2800+(Barton)
Asus Nforce 2IGP (not sure of exact specs but the bios is locked so i cant get to the oc options) 
1x PNY 512mb DDR400 Value Ram
1xInfineon 256mb DDR333 Value Ram
Asus 16x DVD-ROM
48xCD-RW Burner
Turtle Beach Riveria SoundCard(nothing hooked up)
3com Eathernet card(not being used)
Western Digital 120Gb Hard Drive
Ive tried reinstalling Linux and am still getting the same problem. 
Any help would be greatly appreciated.
Thanks

---

### Post by anirban.sam on 2006-02-20
[QUOTE=balance]I recently installed Ubuntu 5.1 from one of the cd's sent to me. The install went fine but now when i login it loads up the desktop and will sit there for a few seconds(the time varies ocasionally) and then the screen flickers goes black and then kicks me back to the login screen. If I repeat this multiple times than it does one of two things:

1. It freezes totally and I have to reboot the computer.
2. It flickers and then comes up with a screen saying that the defaul loader is freezing up. It then attempts to load up the alt. loader which gives me the same options only its in a box with the options at the top in a menu bar. However even when I try logging in from here it still kicks me back to the login screen. 

Right now Im running an HP computer:
Athlon 2800+(Barton)
Asus Nforce 2IGP (not sure of exact specs but the bios is locked so i cant get to the oc options) 
1x PNY 512mb DDR400 Value Ram
1xInfineon 256mb DDR333 Value Ram
Asus 16x DVD-ROM
48xCD-RW Burner
Turtle Beach Riveria SoundCard(nothing hooked up)
3com Eathernet card(not being used)
Western Digital 120Gb Hard Drive
Ive tried reinstalling Linux and am still getting the same problem. 
Any help would be greatly appreciated.
Thanks[/QUOTE]0

Seems to be resolution support problem, shift to any console by ctrl+alt+F2 and type sudo dpkg-reconfigure xserver-xorg

---

