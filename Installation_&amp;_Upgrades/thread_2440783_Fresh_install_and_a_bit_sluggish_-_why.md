---
title: "Fresh install and a bit sluggish - why?"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by phr0stbyte on 2020-04-15
I have just installed Ubuntu Studio 19.10 on a dual Xeon quad system (8 cores). Memory is at 8GB. Everything feels very laggy. It is not extreme, but I would expect that things would be very snappy giving the hardware specks and only running XFCE. Does anyone have any tips on what to look at maybe?

---

### Post by Impavidus on 2020-04-15
Graphics drivers maybe? Have a look at the additional drivers utility.

---

### Post by TheFu on 2020-04-15
*feels very laggy* isn't specific.  Be specific.  Use a stopwatch.  Use the "time" program.  Facts, please.

There are a few things to check.
* log files.  Failing hardware will spew warnings and errors into the logs. Check those.
* RAM use.  What programs are using all the RAM?  Use **top**, **htop**, **vmstat** and free to monitor RAM and buffer use.
* Low disk space.  If /var/ is too full, the entire system will slow down.  
   **df -hT -x squashfs -x tmpfs -x devtmpfs**
* Low swap space. If swap is nearly used up, the entire system will slow as feedback to the user to close some memory hogging programs.  
    **free -hm**
* Using the wrong drivers for network or GPU hardware; What driver and version is used for those devices in your system?  **lshw -C network** and **lshw -C Video**  Install lshw if needed/required.
* Abusing USB devices for OS needs.  Don't run an OS off USB connected storage if you care about performance.

First, let's get some highlevel info about the system.  Install and run inxi
**inxi -Fz**

When you post the requested output, please post both the command AND the output wrapped in _Code Tags_ so the columns line up here like they did in the terminal.  If they don't, the information is too hard to read.

---

### Post by phr0stbyte on 2020-04-17
Never mind. I have redone the system with 20.04 and everything is fine. Not sure what the issue was, but it is running nicely now. I'll take it.

---

