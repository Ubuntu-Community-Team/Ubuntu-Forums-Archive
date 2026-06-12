---
title: "ubuntu no display upon boot"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by Zach USA man on 2011-02-23
so.. finally installed ubuntu on this old compaq, and well, i got no display.

heres what happens:
computer boots up, I choose to run the regular ubuntu and the display dies out about 10 seconds later. I know that its just the display because I can hear the sound ubuntu makes for when it loads up, and I can log in.

graphics are the nvidia geforce 6150 LE

[This]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00702190&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3214102") is the computers specs incase anyone wants to know.

been googling for hours, and nothings worked...
edit: the nvidia 6150 LE works, i was able to get windows xp going on the computer (installed ubuntu via wubi with it)

---

### Post by Hakunka-Matata on 2011-02-23
Zach, do a search on "nvidia" right here in this forum, you'll find loads of information about your situation.  Nvidia can be a bugger...

---

### Post by YesWeCan on 2011-02-23
The standard work-around is to add "nomodeset" to the grub kernel options.
When you are logged in, edit /etc/default/grub and find the command options line, it has nosplash or similar, and add nomodeset to the end, with a space before. Then save it and run 'sudo update-grub' and then reboot.

Once it boots properly, open the system admin hardware drivers menu. This will cause Ubunu to scan your hardware and list available drivers to install. It will recommend one for you graphics card.

---

### Post by wilee-nilee on 2011-02-23
So lets try getting in in safe graphics mode. power on imm hold down the shift tab, at grub menu hit e then navigate to quiet splash with the arrow keys remove it and type in nomodeset, hit crtl+x to boot.

If this gets you in go to the menu and the additional drivers program and see if any can be loaded.

---

### Post by Zach USA man on 2011-02-23
tried the nomodeset and well, enjoy the /dev/sdb1 does not exist. dropping a shell error..
gonna go play the google the solution to this problem game.

---

### Post by Zach USA man on 2011-02-23
woot, the nomodeset did it!
though I had to add my own little solution to the "gave up waiting for root device"

I switched the /dev/sdb1 to /dev/sda1
or was it /dev/sdb or sda
cant remember... thanks though!

---

