---
title: "Nvidia drivers,lag"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by david175 on 2014-03-16
Hello. I recently installed ubuntu 13.10. All i have to say is that it lags so much on pc that it makes windows seem 50x faster. Just opening up the dashboard and typing in something takes up to 20 seconds. My log in screen is blank with only less than a quarter of the screen showing anything. I think this is due to the fact that ubuntu is not picking up my Nvidia drivers Ive been to the additional drivers tab countless times searching for the propriety drivers but I keep getting a error saying no drivers found.IVe used "_*apt-get to install *__*nvidia-current*_" *but that has just gifted me with the infamous black screen after rebooting*
[I][B]
Heres what happens when I run "lspci -nnk | grep -iA3 vga"[/B][/I]

[I]championsonline@ubuntu:~$ lspci -nnk | grep -iA3 vga
00:02.0 [COLOR=#ff0000]VGA[/COLOR] compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a001] (rev 02)
    Subsystem: Lenovo Device [17aa:3607]
    Kernel driver in use: i915
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
--
02:00.0[COLOR=#ff0000] VGA[/COLOR] compatible controller [0300]: NVIDIA Corporation GT218M [GeForce 305M] [10de:0a73] (rev a2)
    Subsystem: Lenovo Device [17aa:3607]
    Kernel driver in use: nouveau
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
[/I]
_***My unity support test results***_

championsonline@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.2.0-devel

Not software rendered:   [COLOR=#ff0000] no[/COLOR]
Not blacklisted:         [COLOR=#00ff00] yes[/COLOR]
GLX fbconfig:            [COLOR=#00ff00] yes[/COLOR]
GLX texture from pixmap:  [COLOR=#00ff00]yes[/COLOR]
GL npot or rect textures: [COLOR=#00ff00]yes[/COLOR]
GL vertex program:       [COLOR=#00ff00] yes[/COLOR]
GL fragment program:     [COLOR=#00ff00] yes[/COLOR]
GL vertex buffer object: [COLOR=#00ff00] yes[/COLOR]
GL framebuffer object:   [COLOR=#00ff00] yes[/COLOR]
GL version is 1.4+:       [COLOR=#00ff00]yes[/COLOR]

Unity 3D supported:      [COLOR=#ff0000] no[/COLOR]

---

### Post by david175 on 2014-03-18
Hello

I recently installed saucy salamander 32 bit Ubuntu. Im dual booting windows 7 and ubuntu 13.10. I used to be one of ubuntu top supporters until I got 13.10.It doesnt want to pick up my Nvidia gpu so as a result it lags terribly. Opening up the dashboard on ubuntu requires great patience as it opens up frame by frame.:( Ive tried running the sudo update Nvidia current  command in the terminal but all thats given me is a blank screen after logging on. Ive also searched for propriety drivers in the additional drivers tab but by Nvidia gpu doesnt show up. Please help:D

---

### Post by deadflowr on 2014-03-18
Please read
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by david175 on 2014-03-18
[h=2]Heres what happens when I run lspci -nnk | grep -iA3 vga[/h]
championsonline@ubuntu:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a001] (rev 02)
Subsystem: Lenovo Device [17aa:3607]
Kernel driver in use: i915

00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)

02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218M [GeForce 305M] [10de:0a73] (rev a2)
Subsystem: Lenovo Device [17aa:3607]
Kernel driver in use: nouveau
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

---

### Post by coffeecat on 2014-03-18
Threads merged. Please do not start different threads on the same problem in different parts of the forum.

It looks as though you have nvidia hybrid graphics. Have a look at Bumblebee:

[http://bumblebee-project.org/](http://bumblebee-project.org/)

I have no experience of this, but someone should be able to help you.

---

