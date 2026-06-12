---
title: "trouble install ubuntu 8.10 to armada 3500"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by yilin on 2008-11-07
ubunto desktop cannot install to compaq armada 3500?

I used the desctop i386 cd. It says:
bios aci must enabled and then keep printing things to the screen (runs very fast, cannot read those binary things).

I checked the ancient laptop. If the bios setting must read  something in the hard drive, then my hard drive doesn't have that compaq service partition. Otherwise, after i put an old hardrive to the machine and get into the bios, I saw ahci is enabled.

The bottom line is: armada 3500 can install debian etch ok.

Anyone can tell me how to install ubuntu 8.10 to my armada 3500?

---

### Post by Partyboi2 on 2008-11-07
With those system specs you might be better off trying to install [[COLOR=Blue]dsl[/COLOR]]("http://www.damnsmalllinux.org/") (darn small linux)

---

### Post by yilin on 2008-11-21
Since 8.10 is impossible to me, I installed debian etch. Which is pretty nice already. My wireless with D-Link DWL-G650 not working and the display was 800x600 rather than the LCD's native 1024x768.

I edited /etc/X11/xorg.conf
set the default depth to 16 instead of 24
and added:

        SubSection "Display"
                Depth   16
                Modes   "1024x768" "800x600"
        EndSubSection

and reboot to got the 'right'(best possible) desplay.

This made me thinking about trying ubuntu desktop 7.10...

This time I still got the wired msg about bios but at least it let me get into the live os where I can install the system. 

The display is still 800x600 at the installation time which was tough since I couldn't see the "forward' button. But anyway I got through the installation and fixed the display like I did for etch. The cool thing was that the wireless worked automatically.

As a c/objec/python programmer, I'd say that my aramada, with etch or ubunto7.10, is not too bad: not that old for coding and debugging (that's way linux:)

Now my problem is:
How to upgrade from ubuntu 7.10 to 8.10 (or is this a bad idea for armada 3500)?

I haven't got the sound work. Any hints (general approach of configuring sound card?)

Thanks

---

### Post by yilin on 2008-11-21
It is not a problem upgrade ubuntu from 7.10 to 8.04. But once it is updated, the system cannot boot: it shows the msg about bios problem and then display a quickly running up scrambling screen..

So the problem started with 8.04, not 8.10. I recalled that armada 3500's display problem with debian lenny, where instead of running scrambling display at boot time, it displays dual images for everything at login screen.

So the root problem maybe inside of debian.

Anyway, if this is only with armada 3500, it simply means armada3500's highest os along debian will be ubuntu7.10/etch. Fair enough for such an antique:)

---

