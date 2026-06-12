---
title: "Problem with real-time clock since upgrading to 17.10"
date: 2017-10-27
forum: Installation &amp; Upgrades
---

### Post by pbmilley on 2017-10-27
I recently upgraded from 17.04 to 17.10 using the software update process. The update completed without any errors, and 17.10 is now running without any major issues. However, I was running a script previously that uses "rtcwake" which has since stopped working. (The script automatically hibernates my laptop after a set period of time in sleep mode, and was working perfectly in 17.04)

In the process of troubleshooting, I discovered that the problem was with rtcwake which is complaining about "/dev/rtc0" missing. 

Here is output from a sample rtcwake command:
```
peter@haven:~$ rtcwake -m no -s 1300
rtcwake: assuming RTC uses UTC ...
rtcwake: /dev/rtc0: unable to find device: No such file or directory

```

I verified that in fact, that directory is missing. Since this was working prior to the upgrade, I have to assume that it was there previously, but I don't know for sure.

In researching the error, I found some suggestions to get further information with "timedatectl" and "hwclock", so here are the results from those commands as well.

"timedatectl":
```
peter@haven:~$ timedatectl
      Local time: Fri 2017-10-27 19:06:26 EDT
  Universal time: Fri 2017-10-27 23:06:26 UTC
        RTC time: n/a
       Time zone: America/New_York (EDT, -0400)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no

```

"hwclock --debug":
```
peter@haven:~$ sudo hwclock --debug
[sudo] password for peter: 
hwclock from util-linux 2.30.1
Trying to open: /dev/rtc0
Trying to open: /dev/rtc
Trying to open: /dev/misc/rtc
No usable clock interface found.
hwclock: Cannot access the Hardware Clock via any known method.

```
Has anyone else experienced any similar issues since upgrading? If not, please offer any suggestions how best to proceed with my troubleshooting. Thanks!

---

