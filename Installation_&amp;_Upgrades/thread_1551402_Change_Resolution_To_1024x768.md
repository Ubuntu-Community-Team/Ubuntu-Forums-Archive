---
title: "Change Resolution To 1024x768?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-08-12
Hello

I'm trying to use the Xubuntu-based BitDefender Rescue Disk, and having an issue. Posting in their forum didn't return anything, so I figured I should ask here next.

Using the default settings, the Rescue Disk starts in 800x600 and complains that the resolution is too low to run the app in graphic mode.

FYI, this servers + monitor run Windows just fine in 1024x768 @ 75Hz, and even higher.

I tried adding "screen=1024x768" to the command-line, to no avail.

FWIW, the default includes "vga=791" but I don't know what it means.

If someone had the same issue, how can I set the resolution to something higher so I can run BitDefender in graphic mode?

Thank you.

---

### Post by lechien73 on 2010-08-12
The "vga=791" switch should set the resolution at 1024x768 with 16-bit colour depth.

You could try some of the other variants:

vga=773 is 1024x768, 8-bit
vga=790 is 1024x768, 15-bit
vga=792 is 1024x768, 24-bit

It would be useful to know what graphics card the server has.

---

### Post by littlebigman on 2010-08-12
Thanks for the tip.

773 didn't make any difference.
790 = error -> prompted me to choose -> chose i/317 (1024x768 @ 16) -> no difference
792 = no difference

It's a compact, desktop [Acer Aspire L100]("http://support.acer.com/acerpanam/desktop/0000/Acer/AspireL100/AspireL100sp2.shtml") with "Integrated NVIDIA® GeForce® 6150 graphics".

Thank you.

---

### Post by littlebigman on 2010-08-12
Not gettting any luck. It seems like BitDefender doesn't like the "Integrated NVIDIA® GeForce® 6150 graphics" included in the Acer Aspire L100, and won't let users change the video settings:

```
# gtf 1024 768 75

# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

# xrandr --newmode "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
Can't open display
```

---

### Post by efflandt on 2010-08-12
Not sure what you are trying to recover, but if you have trouble getting Ubuntu to work, you could always try the good old reliable Knoppix live CD.  When I was trying to identify hardware on an old computer to use for IPCop (firewall/proxy that just returns numbers instead of names for **lspci**) Knoppix 5.1.1 booted into X fine on an old K6-2/400 w/128 MB RAM.  Current Knoppix version from Jan 2010 is 6.2.1.  [http://www.knoppix.net/](http://www.knoppix.net/)

---

### Post by littlebigman on 2010-08-12
Can't do, as I need to use this BitDefender live CD to scan Windows host for viruses. Incidently, BitDefender moved from Knoppix to Xubuntu last year.

More progress... leading nowhere:

```

# echo $DISPLAY
:0.0

# xhost +localhost
No protocol specified
xhost:  unable to open display ":0.0"

```

Read that on Debian/Ubuntu, by default, X is configured with "-nolisten tcp":

```

# ps aux | grep X | grep -v grep
root      2477  0.1  1.7  23552 17056 tty7     Ss+  16:37   0:06
/usr/bin/X11/X -nolisten tcp -auth /var/run/slim.auth vt07

```

So looked for configuration file...

```

# find / -name "gdm*"
/etc/gdm
/var/lib/update-rc.d/gdm
/rofs/etc/gdm
/rofs/var/lib/update-rc.d/gdm

# ll /etc/gdm/
-rw-r--r--  1 root root  126 2010-08-12 18:30 custom.conf
-rw-r--r--  1 root root  132 2008-06-25 02:05 failsafeBlacklist
-rwxr-xr-x  1 root root 8620 2009-03-17 08:59 failsafeDexconf
-rwxr-xr-x  1 root root 8523 2009-11-05 02:48 failsafeXinit
-rwxr-xr-x  1 root root 4559 2009-11-09 07:58 failsafeXServer

# gdmsetup
Command not found

```

Edited /etc/gdm/custom.conf to add this:
```

[Security]
DisallowTCP=false

```

Logged off, logged back on (this live CD is not persistent, so can't reboot and keep settings):

```

# xhost +localhost
xhost:  unable to open display ":0.0"

```

Were there major changes in Ubuntu 9.10 that would explain this permission issue + missing configuration files?

Thank you.

---

