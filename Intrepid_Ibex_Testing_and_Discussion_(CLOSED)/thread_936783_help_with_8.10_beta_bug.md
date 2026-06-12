---
title: "help with 8.10 beta bug"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forcecore on 2008-10-03
I have great problem that i cannot do anything with 8.10 on my main computer and it may stay in final release too. i do not have skills to log them and if i want to i still cannot because of no display.

UPDATE: same issue was with friends 2900xt.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272814)

Please help or ubuntu 8.10 experience may fail on lot of computers.

---

### Post by forcecore on 2008-10-04
bump, has anyone experienced that bug, this may become big problem if not fixed.

---

### Post by Sef on 2008-10-04
> [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/272814]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272814")

Did you correctly report the bug?  (See comment.)

---

### Post by forcecore on 2008-10-04
i have don what i can now but i cannot provide logs if i cannot see display

---

### Post by rbmorse on 2008-10-04
This is already filed as Bug 264462.  The problem will likely affect any user with an ATI R6XX or R7XX video card.  I get my HD3870 going with the following work around:

Boot from the LiveCD. When the display blanks, let the system continue to run.  When the activity LED on the optical drive stops, wait a bit to make sure it's finished. Then, wait a bit more. 

When you're satisfied the LiveCD has finished loading, press the following keys at the same time:

<alt><ctrl><F3>

This will open a terminal screen.  Enter the following commands in sequence. <enter> means press the <enter> key.
```

cd /etc/X11<enter>      <---note the uppercase "X"
sudo nano xorg.conf<enter>
```You will have to use the arrow keys to navigate.  Find the line that starts with  Section "Device"
Below that an indented line that starts with Identifier

Immediately below the Identifier line, insert a new line (indented the same way) that reads
```
Driver    "radeonhd"
```The quote marks (") are required.  When you are finished, that part of the xorg.conf file should look like:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver         "radeonhd"
EndSection
```save the file by pressing the <ctrl> and <o> keys at the same time, then press <enter> to confirm you want to write out the file xorg.conf. Then close the editor by pressing <ctrl> and <x> at the same time. 

Then press the <ctrl><alt> and <F7> keys at the same time.  This should return you to a blank screen as before.

Press <ctrl><alt> and <backspace> at the same time.  This will restart the X server with the radeonhd driver and the display should come up normally. 

Install Ubuntu normally. The installer will remember the LiveCD is using the radeonhd driver and should install that configuration so the above steps should only have to be performed once.

---

