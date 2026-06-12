---
title: "frequency scaling broken since 2.6.32-20"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BackwardsDown on 2010-04-15
Since kernel 2.6.32-20 the frequency scaling on my laptop (intel duo 2 core) is not working anymore. It's stuck on 800Mhz.

On 2.6.32-19 it works fine. Are there more people that have this problem? I could not find much on launchpad.

---

### Post by mc4man on 2010-04-15
Have seen the same on a dell 1300m, though it is random, sometimes will work and sometimes not. (if scaling works then it stays working for the session

Sometimes a reboot will restore, or a reboot to recovery mode, ect.

Has actually happened here since the initial install (.19), though managed to make it go away for about a wk. thru some various methods but seems to have returned with a bit more likelihood of occurring. 

Actually when I booted up this morning was locked at 800, though it is working ok atm after a recovery boot.

I wouldn't doubt it may affect others without notice, if you don't have the applets running it may not become apparent until you do something that would be visibly impacted by the low Mhz, plus that it seems to be a random occurrence (at least here.

---

### Post by mc4man on 2010-04-21
A fresh install the other day seemed to resolve - but yet again ondemand scaling has become nonfunctional here, still somewhat random, but more likely than not.
(meanwhile the conservative mode does function properly

Having gotten tired of this (which may just be a local issue), decided to adjust the up threshold valve, - using 75 instead of the default 95 restores ondemand to expected behavior - *actually think the laptop performs  better in some area's*

Not able to find a file specific to setting a new threshold value permanently so added a for to /etc/init.d/ondemand. (if there is a better way would be interested

Added the blue (decided to go with 65

```
case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
[COLOR="Blue"]
        for CPU_THRESHOLD in /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n 65 > $CPU_THRESHOLD
	done[/COLOR]
	;;
    restart|reload|force-reload)
```

Edit: after several days with lower threshold can say that the overall performance on laptop is better, firefox is most definitely improved, particularly when scrolling on certain pages

---

