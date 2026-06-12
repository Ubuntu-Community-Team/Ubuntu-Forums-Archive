---
title: "problem with wifi / rfkill and uptime"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by mkris23 on 2010-10-11
My wifi (atheros) was working fine when i was using lucid. Today, i ran an upgrade to maverick, and my wireless has stopped working. A fair amount of time was spent googling and i'm pretty much clueless. i've run sudo rfkill list all some five times and most times teh cursor would just keep blinking. one time, i got  a response saying that my bluetooth was hard blocked and my wireless was softblocked. i tried sudo rfkill unblock all but the cursor would just keep blinking and nothing would happen. i even tried leaving it on in a terminal window for about half an hour and nothing happened.

on a related note, when running uptime, the load that is showing is very very high and possibly wrong, and it keeps increasing with time. 

 11:01:48 up 26 min,  3 users,  load average: 5.17, 5.06, 3.65

theres nothing running on my system except firefox and transmission. 

any help would be really appreciated. i'm stuck here.

---

### Post by mkris23 on 2010-10-11
bump. sorry. really need this help.

---

### Post by ricarribe on 2010-10-20
Hi! I've got the same situation here when I did an update from Lucid to Maverick. I've found this problem is caused by the kernel version 2.6.35, or it seems so. At least, when I boot Maverick with kernel 2.6.**32** (choose it from grub menu), Network Manager works fine and shows up all wifi networks.

---

### Post by dewert on 2010-10-24
Hmm... interesting.  I'm having the same problem with an iwl3945.  The 32-25 kernel works for me too.  I'm using wicd, so it's not a NM issue, but I think that was obvious.

Anyone filed a bug report for this yet?  I think I will.

---

### Post by dewert on 2010-10-24
Ok, bug posted: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665993)

---

### Post by ricarribe on 2010-10-24
Thank you, dewert! I've already subscribed to your bug report. If I find some work out I will post it here.

---

### Post by dewert on 2010-10-29
Just to report back for anyone who's stumbling upon this, a solution of some sorts has been found by @klerfayt and @ricarribe over on the bug report.

To summarize:

If you have an Acer, you may want to try
```
sudo modprobe acer-wmi
```
If this works, add
```
acer-wmi
```
to your **/etc/modules**

If you have an HP, adding
```
blacklist hp_wmi
```
to your **/etc/modprobe.d/blacklist.conf** seems to do the trick.
This has resulted in poor connection speeds for @klerfayt, but mine seems to be ok, though I don't have a number to back that up.  With my router, I wouldn't be too hasty to conclude that it has anything to do with the laptop, anyway :P

---

### Post by ricarribe on 2010-10-29
dewert, thank you for reporting the work around here!

For those who use acer laptops, it's a good idea to restart Network Manager ('sudo restart network-manager') after trying 'sudo modprobe acer-wmi'. I think this will only work until you do not turn off the computer. So I added the line 'acer-wmi' to '/etc/modules', as dewert said, cause the module would be automatically loaded every time you boot the system.

---

