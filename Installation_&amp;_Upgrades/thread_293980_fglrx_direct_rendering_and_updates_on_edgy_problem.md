---
title: "fglrx direct rendering and updates on edgy problem"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by eldragon on 2006-11-05
since i upgraded to edgy from dapper. ive been having this small problem:
every time there is an update, after installing, it kills direct rendering.
and i have to do an apt-get install --reinstall xorg-driver-fglrx to get Direct rendering running again.
so my question is: is anyone aware of this? has anyone had this problem? is it being worked on? should i wait for a fglrx driver update?

my gpu is a radeon x600.

btw: im SOOO happy with edgy, they fixed palm sync! :D

---

### Post by clever forum name on 2006-11-08
My system has an X600 ATi card as well. In my case I needed to augment the xorg.conf in order to get the right drivers loaded.
You may have seen the addition: 
> Section "Extensions"
        Option      "Composite" "0"
EndSection

It is in many of the postings in these forums. 

In any case, I was under the impression that I needed to reinstall, but all  I may have been missing was this addition to the configuration file. Now that all has been installed I am getting very low frame rates. 

> 
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 2.0.6119 (8.30.3)

$ lspci|grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]

$ glxinfo |grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON X600 Generic

$ glxgears -printfps
1253 frames in 5.0 seconds = 250.536 FPS
1250 frames in 5.0 seconds = 249.984 FPS


How about you? Any better? So far most of the postings related to Edgy are for nVidia cards. I'd appreciate it if you would post your output with the glxgears cmd, for comparison.
_CFN

---

### Post by eldragon on 2006-11-13
ok, here's my info.

whats that difference in driver vesion im seeing? as far as im concerner ive got everyithing upgraded :(


eldragon@emmet:~$ glxgears
1253 frames in 5.0 seconds = 250.495 FPS
1250 frames in 5.0 seconds = 249.985 FPS
eldragon@emmet:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO Generic
OpenGL version string: 2.0.6011 (8.28.8)

eldragon@emmet:~$ lspci|grep VGA
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]
eldragon@emmet:~$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON X600 PRO Generic

---

### Post by W.McL on 2006-11-14
I probably got the same problem. To me it seems like messed up dependencies:
Apt reports a dependency mismatch for fglrx-kernel-2.6.17-10-386. It demands  xorg-driver-fglrx (= 8.28.8-1), but installed is version 7.1.0-8.28.8+2.6.17.6-1.

Because of the unmatched dependencies the package is removed during an upgrade and direct rendering is gone after a reboot.

I kind of "solved" the problem by manually installing the deb package, which is located in /usr/src after each upgrade. Because of the version conflict I have to tell dpkg to ignore that problem:
```

$ sudo dpkg -i --ignore-depends=xorg-driver-fglrx /usr/src/fglrx-kernel-2.6.17-10-386_8.28.8-1+2.6.17-10.33_i386.deb

```

It's not a clean solution and it's rather annoying to have to do that after each upgrade or software installation, but at least it makes direct rendering work.

---

