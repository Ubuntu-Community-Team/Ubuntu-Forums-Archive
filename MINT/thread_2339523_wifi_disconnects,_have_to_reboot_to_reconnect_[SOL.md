---
title: "wifi disconnects, have to reboot to reconnect [SOLVED]"
date: 2016-10-09
forum: MINT
---

### Post by jim97321 on 2016-10-09
LinuxMint is built from Ubuntu and I am thinking that this may fix Ubuntu (maybe even Debian) wireless problems too.

My LM post is:
forums.linuxmint.com/viewtopic.php?f=53&t=231490

---

LinuxMint 18 Mate,64-bit:


My wifi was dropping after random time intervals and I could not turn it back on at all. This was making me reboot my system and this was driving me mad. After-all, I used to run linux for months without rebooting.


I run "iwconfig"in a terminal and it indicates:
Power Management on


(-- Running "sudo iwconfig wlp16s0 power off" would turn "Power Management off", but in a couple hours it would come back on. (Only a temporary fix.)  Change "wlp16s0" to your wifi card.  type "sudo iwconfig" then hit TAB TAB.  You will find your card populates (or gives several to chose from).  Finish with "power off".  Again, this was only a temporary fix and it would reset to an "on" state after a period of time.


Another part of the fix was to change IPv6 settings to Ignore.


I altered all instances of "power on;" in"/usr/lib/pm-utils/power.d/wireless" to "power off;".


I extended the lease time to 1000-hours and changed "power on: to "power off:"in "var/lib/NetworkManager/dhclient-wlp16s0.conf".


I also extended the lease time to 1000-hours and changed "power on: to "power off:" in "/etc/dhcp/dhclient.conf".


Finally, after discovering the below, I reversed all the above fixes and incorporated just the one fix below! --)


Using "Search"(application), I searched for ".conf" in "File System"and found the file
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf


This contains:
[connection]
wifi.powersave = 3


Thinking this controls "Power Management on", above, I changed the 3 to 0.


Now when I boot and run "iwconfig" I find:
Power Management off


I can even switch between all the access points without problems.


I think this is going to take care of my wifi being dropped and not being able to turn it back on without rebooting.


(I just hit 24 hours with this being the only setting, wifi has been working just fine, so I am submitting this as a solution.)

---

### Post by howefield on 2016-10-10
Thread moved to the "*MINT*" sub forum.

---

### Post by jeremy31 on 2016-10-10
Jim, does the power management switching to on happen while plugged in?  It is not supposed to

What happens if you set ```
wifi.powersave = 1
```

This will not affect Debian as it was a change in Ubuntu network-manager package from [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1557026](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1557026)

---

