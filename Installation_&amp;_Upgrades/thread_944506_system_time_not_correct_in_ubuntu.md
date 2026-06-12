---
title: "system time not correct in ubuntu"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2008-10-11
i have set up ubuntu 8.1 on an external usb hdd, and whenever i load up the OS, the system time changes by itself.

at first when i set up ubuntu, i set my local as GMT -4 (ny), but it took the bios time and subtracted 4 from it...

then i tried setting the local to GMT and changed the time to the correct time, but whenever i boot into vista, the time becomes GMT + 4.

not sure what's going on here or how to fix it, but it's annoying.

---

### Post by zero7404 on 2008-10-11
bump

when i connect to the internet the time resyncs to the correct time, but when i go back into windows, i get a time that's not correct.

---

### Post by zero7404 on 2008-10-11
after some searching, i did this:

sudo ntpdate time.nist.gov

looks like the time is now correct in ubuntu, going to check it with vista on my next reboot.
i think the issue comes from vista thinking that the time set in the bios is localtime and not utc, whereas in linux it was assuming the bios time is set to utc.

---

### Post by zero7404 on 2008-10-13
here i go again talking to myself on this forum....

the above steps were tried and didn't work. but i found something that did work, posting it here to help those that need it because nobody helps me with my posts on this forum....

i used solution C in this article and the time appears correct whenever booting into either OS:

[http://forum.insanelymac.com/index.php?automodule=blog&blogid=284&showentry=408](http://forum.insanelymac.com/index.php?automodule=blog&blogid=284&showentry=408)

---

