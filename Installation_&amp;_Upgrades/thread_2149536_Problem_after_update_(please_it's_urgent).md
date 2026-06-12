---
title: "Problem after update (please it's urgent)"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by zara89 on 2013-05-29
I'm pretty new to linux, so I do not know the right terms. I have this problem and a bit in a hurry because I have to deliver a job on Monday and I need to start again to work!

I have Ubuntu 12.04 [the screen says Welcome to Ubuntu 12.04.2 LTS (GNU / Linux 3.5.0-31-generic x86_64)]
Last night I was working...while writing and surfing on the internet, the window of the updates came out. I have accepted and as I usually do, all right ... then once finished to work i made a reboot as the updates asked...and now it stops on the loading screen (the one with violet background, the word "ubuntu" and dots) and does not move from there! I can open with ALT + F4 the command line without a graphical environment, but I do not know what to do! I have to uninstall the latest updates? and how can I do this?:confused:
[edit] now also ALT+F4 does not work !!!!!! ???? it all stops with the "ubuntu* ....." screen!!! dots are orange, and does not change color.....but if i press the shutdown button they change!!!

please help, it is urgent!

---

### Post by Cheesemill on 2013-05-29
Try choosing an earlier kernel to boot into on the Grub menu screen (the one before the dots).

---

### Post by zara89 on 2013-05-29
i tried...i could choose

"Ubuntu, with Linux 3.5.0-31-generic"
"Ubuntu, with Linux 3.5.0-31-generic (restore mode)"
"Previous Linux versions"

so i chose previous version, and i had:
"Ubuntu, with Linux 3.5.0-23-generic"
"Ubuntu, with Linux 3.5.0-23-generic (restore mode)"

i tried the first one, but it still stops with the "ubuntu* ....." screen....at least i can press ALT+F4 and have a command line now...but what can i do?

---

### Post by zara89 on 2013-05-29
i tried to boot "Ubuntu, with Linux 3.5.0-23-generic", but it still stops with the "ubuntu* ....." screen....at least i can press ALT+F4 and have a command line now...but what can i do with this? is there a way to remove last updates?

---

### Post by fantab on 2013-05-29
A couple of possible reasons could be:
1. that some package upgrade did not go well.
2. there could be some filesystem errors.

Boot Ubuntu into 'Recovery Mode'. First try "Ubuntu, with Linux 3.5.0-31-generic (recovery mode). A Simple menu will open. Select 'dpkg - Repair broken packages' and hit enter key. Then run 'fsck - filesystem check'. Once done boot into normal boot.

If it doesn't work with 3.5.0-31 then try with "Ubuntu, with Linux 3.5.0-23-generic (restore mode)".

---

### Post by grahammechanical on 2013-05-29
You could try Recovery Mode and at the recovery mode screen select Resume. If you get to a working desktop open Additional Drivers and activate a video driver.

Regards.

---

