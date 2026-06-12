---
title: "Help just install 10.04 Ubuntu on compaq laptop"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by matrix06 on 2011-12-07
I installed Ubuntu to be man operat. Os and 3/4 way thru error pops up so I Re burn a new coppy
And try to finish install now on boot I get a blank screen with a blinking curser
  I can't install windows to see what went wrong  because the format is no longer in a
Format comp to windows what do I do?

---

### Post by lkraemer on 2011-12-08
The best ting to start with is to Boot from a Ubuntu 10.04 LTS (Long
Term Support) LiveCD.  If everything functions properly from the LiveCD
Boot, then you can try the install.  If the LiveCD has problems, it could
be a bad ISO download, or maybe a problem with your Computer's CDROM Drive.
Boot the ISO on several Computers and see what happens.  You can verify
the ISO's MD5SUM or SHA256 Hash Code to make 100% sure it's a VALID ISO.
If the Video is messed up during install, there are Boot CHEAT CODES that
you can try....

> 
Some systems (especially laptops) that have a native resolution that is not a 4:3 ratio (i.e. not for example 800x600 or 1024x768) may have a blank display after the installer has been booted. In that case adding the boot parameter vga=788[10] may help. If that does not work, try adding the boot parameter fb=false.

If your screen begins to show a weird picture while the kernel boots, eg. pure white, pure black or colored pixel garbage, your system may contain a problematic video card which does not switch to the framebuffer mode properly. Then you can use the boot parameter fb=false to disable the framebuffer console.

So, I'd suggest noplymouth, xforcevesa, nomodeset, vga=788, fb=false or a combination of these as needed.  Try them one at
a time from the LiveCD.

REF:
[http://translate.google.com/translate?hl=en&sl=de&u=http://wiki.ubuntuusers.de/booten&ei=O87gTtv_EqOTiALBg82NDw&sa=X&oi=translate&ct=result&resnum=10&ved=0CGsQ7gEwCTgK&prev=/search%3Fq%3DUbuntu%2B10.04%2BBoot%2BCheat%2BCodes%26start%3D10%26hl%3Den%26sa%3DN%26biw%3D1280%26bih%3D883%26prmd%3Dimvns](http://translate.google.com/translate?hl=en&sl=de&u=http://wiki.ubuntuusers.de/booten&ei=O87gTtv_EqOTiALBg82NDw&sa=X&oi=translate&ct=result&resnum=10&ved=0CGsQ7gEwCTgK&prev=/search%3Fq%3DUbuntu%2B10.04%2BBoot%2BCheat%2BCodes%26start%3D10%26hl%3Den%26sa%3DN%26biw%3D1280%26bih%3D883%26prmd%3Dimvns)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)
[https://help.ubuntu.com/10.04/installation-guide/index.html](https://help.ubuntu.com/10.04/installation-guide/index.html)
[https://help.ubuntu.com/10.04/installation-guide/i386/index.html](https://help.ubuntu.com/10.04/installation-guide/i386/index.html)
[https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html)


When you Install, hopefully the Video will be properly detected by the
LiveCD Boot and you will have a functional system.  (Sometimes you might have
to install from the Alternate ISO, but that means you'll be setting everything
up from scratch, which is most likely not for new Linux Folks.)

As soon as you get a Hard Drive install, connect by Ethernet and do an UPDATE of
the system.  Then select the Menu Option to update Hardware Drivers. That should
fix most Video and Wifi Problems.

So, start by doing a VERIFY of the ISO's MD5SUM.  Then boot the ISO on several
Computers to see how it works, then Install on one......

If the Install is screwed up, you can't just finish the install.  You have
to start over from the Beginning, just like Wonders..........


Larry

---

