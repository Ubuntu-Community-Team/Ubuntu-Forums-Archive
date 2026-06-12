---
title: "/etc/rc.local not working?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrickfromspain on 2008-10-08
Hi there!

I've put the following lines into /etc/rc.local

echo "10:19 8:19 6:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls 
echo "10:19 8:19 6:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
/etc/init.d/bluetooth stop
setkeycodes e002 91
modprobe -r rfcomm
modprobe -r bnep
modprobe -r ata_generic

exit 0

thing is that the first two echo lines work fine, but the lines after that don't seem to be working.

Any ideas? is there any log file I can look into? Anyone with the same problem?

If I run the lines one by one, they work fine and do what I expect to.

EDIT: it was working fine in hardy

---

### Post by alastair on 2008-10-08
Does it work without the "bluetooth" line?

What about just blacklisting the modules?

Alastair

---

### Post by taavikko on 2008-10-08
Can confirm this behaviour, I have a simple wget command, which doesn't get executed...

---

