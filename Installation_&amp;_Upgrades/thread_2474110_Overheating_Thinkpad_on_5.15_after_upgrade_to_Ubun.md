---
title: "Overheating Thinkpad on 5.15 after upgrade to Ubuntu 22.04"
date: 2022-04-22
forum: Installation &amp; Upgrades
---

### Post by ninoivanov on 2022-04-22
Hi everyone,

Just a note to everybody: on a Lenovo X201, after upgrade to 22.04 from 20.04, the machine overheats and forcibly shuts down. Now, this is plainly stupid and the machine never did it before.

Various Thinkpad control utilities no longer seem to work, though two things do seem to work:

thinkfan

tlp

as root:  echo level 7 > /proc/acpi/ibm/fan
as well as limiting your CPU speed to 1GHz, again as root:

echo 1000000 > /sys/devices/system/cpu/*/cpufreq/scaling_max_freq

(it will put it on 1.2 GHz actually)

So, there are a couple of workarounds, none of them particularly great - I post this here for other unfortunate souls.

EDIT:

OK, having run (Alt-F2) gnome-session-properties, I added a script with the following contents to be executed on login - that does indeed help, adjust as needed:

#!/usr/bin/sh
for f in /sys/devices/system/cpu/*/cpufreq/scaling_max_freq; do
  /usr/bin/sudo /usr/bin/sh -c "/usr/bin/echo 1000000 > $f"
done
sudo /usr/bin/sh -c "echo level full-speed > /proc/acpi/ibm/fan"
/usr/bin/sleep 2
/usr/bin/sudo /usr/sbin/tlp start
/usr/bin/sudo /usr/sbin/thinkfan

---

