---
title: "upgrade makes 12.04 shutting-down slowlier ?"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by dschinn1001 on 2012-05-29
Hello all !

On 24th/25th May I made with precise pangolin
an usual
apt-get dist-upgrade

Result is, that ubuntu is shutting down slowlier than before ???
Shutting down is lasting now 30 to 40 seconds. Before that dist-upgrade
shutting down was lasting at maximum 3 to 7 seconds (yes with ssd-disk).

Thanks for reply.
Happy coding.
dschinn1001

---

### Post by nipunshakya on 2012-05-29
In my case, shutting down was within 3 seconds. After a couple of updates, now its not uniform...sometimes 5-10 secs and sometimes more than that... Same problem here...but thats just a minor thing i guess...

---

### Post by dschinn1001 on 2012-06-04
Hello !

With upgrade of 3th June, this Problem is solved.
Pangolin is booting quick and shutting down quick again.
Remains only the USB-Problem, auto-mount is not working any more ?
Means there is not popping up a window with filesystem-message, when
I plugged usb-drive or usb-disk in. I miss that ... would like to have it back,
cause then you know, that usb is properly working.

Regards.
dschinn1001

---

### Post by dschinn1001 on 2012-06-05
Hello back !

USB-problem with extern hard-disks and extern dvd-drives seems to be solved. 
But only I cannot setup hp-printer ?
USB-printer is not recognized ?

Thanks for good upgrade so far !

Regards.
dschinn1001

---

### Post by dino99 on 2012-06-05
which hp printer ?

into a terminal, run:  sudo update-usbids && sudo update-pciids

then logout/in

---

### Post by dschinn1001 on 2012-06-05
sorry ! problem with hp-printer is solved.
there was python-qt missing as package.
And ... <blush> usb-cable non-visible was unplugged at rear-side of printer.
Now anything works.
hp-window was popping up for installation of driver.
if not window pops up then
sudo hp-setup -i 
is the solution.

---

