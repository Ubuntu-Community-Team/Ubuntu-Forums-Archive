---
title: "Ubuntu 10.1 install on Dell D800 -&gt; fuzzy icons"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by pacman5 on 2011-03-01
Am trying to run Ubuntu from the CD on a Dell Latitude D800 laptop that a friend gave me. A Suse Linux installation is currently on the laptop and appears to run OK and its desktop looks normal with normal buttons and icons.

The Ubuntu boot from the CD appears to run normally but all the icons and buttons on the desktop and the taskbar appear fuzzy/fragmented (that's the best way I can describe it). The menu texts appear normally. Otherwise the system seems to work normally. I can select menu items and they do what they should do, etc.

I've tried fiddling with the screen resolution but that doesn't improve anything. 

I've tried the installation with 10.1 and 10.04LTE but the result is the same: fuzzy icons and buttons.

Can anyone here tell me how to go about the diagnosis or what the cause might be ?

---

### Post by eb207 on 2011-03-02
I have the same problem, also on a Dell latitude D800. ubuntu 10.10, 32 bit. The icons display fuzzy or garbled, but everything else seems to be fine. Changing screen resolution doesn't help.

---

### Post by pacman5 on 2011-03-03
I've just found the solution myself. Install the nVidia driver as follows:

[LIST]
[*]Install the Ubuntu system to the hard drive(the solution won't work if you run it from the CD because the newly installed driver simply disappears when you shut down the system). I installed Ubuntu 10.04LTE.
[*]-> System -> Administration -> Hardware Drivers. It will offer you the nVidia driver as "Recommended". Follow the instructions to install it.
[*]-> Restart the system.
[*]-> Problem solved. The icons and buttons now appear normal.
[/LIST]

---

### Post by eb207 on 2011-03-04
Thanks for the info. I find that this does not work for Ubuntu 10.10. However I then tried 10.4 LTE, and it does work for me. Which is good enough. Thanks!

---

### Post by pacman5 on 2011-03-04
Good to hear. You're welcome.

I can't get over Ubuntu. This is the third time I've installed it on an ancient (= ancient IT-wise) computer that someone had cast aside and each time I've ended up with an excellent machine that is perfectly adequate for SOHO tasks. It may not be so snappy when processing big video files but heck........

By the way, my cast-off Dell Latitude D800 turned out to contain a wireless card which I activated by downloading the Broadcom legacy driver, again with -> System -> Administration -> Hardware Drivers.

Heck, there's probably a coffee machine and a dog-groomer in there if only I install the drivers.

---

