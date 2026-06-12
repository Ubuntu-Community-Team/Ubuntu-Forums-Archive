---
title: "Black Screen With Typing Cursor Yet Totally Unresponsive"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by jac000 on 2016-10-28
[ATTACH=CONFIG]271833[/ATTACH][ATTACH=CONFIG]271834[/ATTACH]
Computer/Bios Info       What I See When Booted

I have installed a Ubuntu server to mess around with onto my old computer, everything booted correctly and the installation process went through without any problems. I did not install a GUI so I knew I would get a command line version. When I pressed continue and rebooted I got a black screen with the flashing typing cursor. The computer is not frozen, however, it is unresponsive and does not register that I am typing/ doing anything. When I press the power button the "Ubuntu 16.10" text shows up in the middle of the screen before the computer turns off. Have I done something wrong? Is this what I am supposed to see and I'm being a complete idiot? I have never used an operating system like this before (I have used Linux for a while though) and am wondering how to make it respond.

Thanks for any help!

*EDIT* Reinstalled and now I get this
[ATTACH=CONFIG]271835[/ATTACH]
The Error Message is this: 

[COLOR=#000000][FONT=&quot][ NUMBER] [drm:intel_set_pch_fifo_underrun_reporting [i91511]*ERROR*uncleared pch fifo underrun on pch transcoder A[ NUMBER] [drm:intel_pch_fifo_underrun_irq_handler [i91511]*ERROR*PCH transcoder A FIFO underrun

[/FONT][/COLOR]Different number every time I restart, Their are other people who had this error message but they all have it in combination with other messages. 
[COLOR=#000000][FONT=&quot][ 1.816597] [drm:intel_set_pch_fifo_underrun_reporting [i91511]*ERROR*uncleared pch fifo underrun on pch transcoder A[ 1.816611] [drm:intel_pch_fifo_underrun_irq_handler [i91511]*ERROR*PCH transcoder A FIFO underrun[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-10-29
jac000; Hello;

A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a black screen or show corrupted splash screen. See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter.

If you are then able to boot to a terminal. we work on getting a graphic's driver installed .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by jac000 on 2016-10-29
Thanks but I have run Ubuntu on this computer before and problems only started when I attempted to install a server, I'll try this anyway, though.

---

