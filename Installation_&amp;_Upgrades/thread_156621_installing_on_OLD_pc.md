---
title: "installing on OLD pc"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by rmbell on 2006-04-07
so ive got a friends 200mhz with 16mb ram pc here and ive been trying to get ubuntu on it. it hangs at the "Ramdisk: compressed image found at block 0" so i checked a verbose on it and its trying to write the ramdisk to ram that doesnt exist and it causes a kernel panic. so is there anyway to cut down the installer's initrd size or avoid this problem? ive tried various boot options and parameters like "server ramdisk_size=8000 root=/dev/ram" and tons of variations on that. I know that isolinux works with the pc since i was able to succesfully install Slackware 10.1 on it, but i'd much rather prefer to use ubuntu.

---

### Post by rado_london on 2006-04-07
I dont know how to do that but if you want to use any GUI on this machine you will be in trouble. It is too old. All it needs is ram.


Good luck

---

### Post by rmbell on 2006-04-07
i dont plan on even installing x :)

---

### Post by MonolithTMA on 2006-04-07
[QUOTE=rmbell]so ive got a friends 200mhz with 16mb ram pc here and ive been trying to get ubuntu on it. it hangs at the "Ramdisk: compressed image found at block 0" so i checked a verbose on it and its trying to write the ramdisk to ram that doesnt exist and it causes a kernel panic. so is there anyway to cut down the installer's initrd size or avoid this problem? ive tried various boot options and parameters like "server ramdisk_size=8000 root=/dev/ram" and tons of variations on that. I know that isolinux works with the pc since i was able to succesfully install Slackware 10.1 on it, but i'd much rather prefer to use ubuntu.[/QUOTE]


Here's a thread from the Damn Small Linux board about an older system. You could try the frugal installation, but I'm not sure how well it will work with 16 megs of ram.
[URL="http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=22;t=12089"]
http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=22;t=12089[/URL]

I've never tried Slackware, so I'm not sure how DSL would compare, but it has a tiny footprint. It's definitely not Ubuntu, but it's pretty cool.

---

### Post by rmbell on 2006-04-07
i've tried DSL, its not anything special. i'm determined to install a debian based system, i can't function without apt-get anymore :P

---

### Post by MonolithTMA on 2006-04-07
[QUOTE=rmbell]i've tried DSL, its not anything special. i'm determined to install a debian based system, i can't function without apt-get anymore :P[/QUOTE]


I haven't played with DSL much, but it seems to let you install apt-get.

---

### Post by rmbell on 2006-04-08
i remembered it was based on knoppix, then i remembered again that knoppix was based on debian. i might have to give it a try again... its been awhile :S thanks so much for the ideas MonolithTMA

---

### Post by MonolithTMA on 2006-04-08
[QUOTE=rmbell]i remembered it was based on knoppix, then i remembered again that knoppix was based on debian. i might have to give it a try again... its been awhile :S thanks so much for the ideas MonolithTMA[/QUOTE]

It's worth a shot. I installed it on a 256 meg usb 2 thumb drive to play with it at home and at work. I'm still amazed that I can boot from a thumb drive! :-)

---

