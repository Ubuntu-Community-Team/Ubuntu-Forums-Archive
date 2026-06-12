---
title: "[SOLVED] Blank Video after text mode"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by dgtldaydrmr on 2007-09-12
After issues with the live CD setup I went with the alt install.
Everything went smooth but after installation was completed it loads up and the screen goes blank.
I can login blindly with my user name and pass and hear the logon sound but video remains black.

I will be working on it now but I figured I would leave a thread here to possibly speed up my troubleshooting.

Also a side note:
A error message flashes very fast when it boots and i think it is something about unable to allocate memory... I think it's related to the 1gb intel turbo cache. I could be wrong.

Toshiba Qosmio F40
2.2 intel C2duo
2GB mem
100gb 7,200 sata HDD
GF 8600m GT video

If there is any additional info that would help let me know.

Thanks in advance!

---

### Post by Pumalite on 2007-09-12
Get a command line: Ctrl+Alt+F1
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver; then: startx

---

### Post by dgtldaydrmr on 2007-09-12
Perfect!
Thanks!
I remember needing to do that for  my other notebook but I forgot about it.

---

### Post by Pumalite on 2007-09-12
You are welcome. Have fun!

---

