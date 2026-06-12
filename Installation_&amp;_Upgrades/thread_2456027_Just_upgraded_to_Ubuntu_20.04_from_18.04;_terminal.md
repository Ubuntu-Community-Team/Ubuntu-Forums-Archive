---
title: "Just upgraded to Ubuntu 20.04 from 18.04; terminal bell not working"
date: 2021-01-02
forum: Installation &amp; Upgrades
---

### Post by chopra on 2021-01-02
Hi Guys,
I am using a Toshiba Tecra and I had Ubuntu 18.04 LTS installed, and I just upgraded to 20.04.
Most things work fine, I have sound in general (youtube videos play) but my terminal bell stopped working after the upgrade.

Normally, nano gives a "ding" noise when a file is not writable, and it stopped doing that. Emacs and vim also don't make noise anymore, like when I try to scroll past the beginning or ending of a buffer.
Bash does not make noise upon tab completion. I tried:
sudo vi /etc/inputrc
and uncommented 
set bell-style visible
which I thought would cause the screen to flash, but it does not.

I tried the command:
echo -e '/a'
and the command:
echo ^G
both of which should give a terminal bell sound, and neither did.

I also tried editing the modprobe file:
sudo vi /etc/modprobe.d/blacklist.conf

and commented out the line:
blacklist pcspkr

but this did not help.

When I open up my terminal preferences, I see that 
sound: terminal bell is checked.

Not sure what else to try.
Thanks, Chopra

---

### Post by chopra on 2021-01-21
Found the problem. I forgot to mention, I was using the cinnamon desktop. Once I switched to GNOME, the problem vanished.
Somehow, cinnamon doesn't like the terminal bell on my machine in the new version.

---

