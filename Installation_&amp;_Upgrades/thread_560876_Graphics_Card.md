---
title: "Graphics Card"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by barqers on 2007-09-26
Now I know there are like a billion topics and things, but I can't figure what's wrong. When I try to install my ati driver for my ati radeon x1300 pro video card it doesn't really work...it works in the sense that the computer sees the card and I have the fglrx drivers installed, but when I even try and play super tux it is unbelievable, it's like trying to play a game with a card make 40 years ago.

Anyways I tried to install the card via the instructions: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Anyways I get to the point of 
> sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

And I get this:
>  Data incomplete in file /etc/X11/xorg.conf
        At least one Device section is required.
Data incomplete in file /etc/X11/xorg.conf
        At least one Screen section is required.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.


Anyways all that is in my xorg.conf file is > Section "Extensions"
        Option      "Composite" "disable"
EndSection

Why is it so empty?... And also when I check my restricted drivers it says it is not in use and in fglrxinfo it says: > Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


Any who can someone guide me through installing my card, I can't even play supertux this is ridiculous Dam you ATI

Thanks guys

---

### Post by Hhkmac on 2007-10-02
Hiya everyone... total noob... and I have the same problem with the same card.... can anyone help?:confused:

---

### Post by ambien on 2007-10-03
That guide didn't work for me either. I finally did get mine working from an Ubuntu Staff member post somewhere on this forum...will post it if I find it.

---

