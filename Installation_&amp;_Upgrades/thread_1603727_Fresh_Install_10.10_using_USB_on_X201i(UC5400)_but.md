---
title: "Fresh Install 10.10 using USB on X201i(UC5400) but can't start X"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Hooman on 2010-10-23
My ThinkPad 201i, 2G memory, UC5400 1.2G CPU with Win7 preinstalled.
Below is the detail what I have done:

Follow the official installation instruction.
1. I created USB drive with AMD-64 image.
2. I tried live CD, everything seems OK except the sound.
3. I Installed ubuntu in new partition( /boot 256M, swap 2G, / 20G /home 80G)
4. After restarted, I couldn't enter X-win, but I can login into tty1. About 2-mins later, It was dead with a black screen.

The last message was:
```
ppdev: user-space parallel port driver
```

As some artical suggested, I added "i915.modeset=0" in the GRUB LINUX parameter. After restarted, the "black screen" problem fixed, although the message "ppdev: user-space parallel port driver" appeared with screen blink.

But, I still can't enter X.
The last lines in /var/log/Xorg.0.log were
```

(EE) open /dev/fb0: No such file or directory
(EE) intel(0): No kernel modesetting driver detected.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
      at http://wiki.x.org
 for help.

Please also check the log file at .....
...

```

Any suggestion to resolve it:confused:?

---

### Post by Hooman on 2010-10-23
BTW, I have also done "apt-get upgrade" and BIOS upgrade.
Now my kernerl version is 2.6.32-25-generic
My BIOS version is 1.22...

---

### Post by Hooman on 2010-10-23
It look's like this bug.
[URL="https://bugs.launchpad.net/oem-priority/+bug/554569"]https://bugs.launchpad.net/oem-priority/+bug/554569
[/URL]

Is it really fixed in 10.10?
Any way, since the live CD mode can work, I compared the two /var/log/Xorg.0.log

Everything are same until Loading /usr/lib/xorg/modules/libfbdevhw.so
Then, the failed one shows:
(EE) open /dev/fb0: No such file or directory
(EE) intel(0): No kernel modesetting driver detected.
the live CD one shows:
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
.....
(II) intel(0): Creating default Display subsection in Screen section "Default Screen Section" for depth/fbbpp 24/32
....

---
Still have no solution :(

---

### Post by Hooman on 2010-10-24
Anybody can help?

---

### Post by pmurk on 2010-10-25
I had the same problem on an Samsum X360 laptop when upgrading 10.04 -> 10.10.
Fixed it with 

[LIST=1]
[*]following [http://ubuntuforums.org/showthread.php?t=1604337](http://ubuntuforums.org/showthread.php?t=1604337) and created new xorg.conf
[*]updated /etc/default/grub
[LIST=1]
[*]changed 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
[/LIST]
 
[*]ran sudo update-grub
[*]and was happy again.:)
[/LIST]

---

### Post by Hooman on 2010-10-26
> **pmurk said:**
> I had the same problem on an Samsum X360 laptop when upgrading 10.04 -> 10.10.
Fixed it with 

[LIST=1]
[*]following [http://ubuntuforums.org/showthread.php?t=1604337](http://ubuntuforums.org/showthread.php?t=1604337) and created new xorg.conf
[*]updated /etc/default/grub
[LIST=1]
[*]changed 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
[/LIST]
 
[*]ran sudo update-grub
[*]and was happy again.:)
[/LIST]

Dear pmurk,
I followed your guidance and created a new xorg.conf, and changed 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor".

But it didn't work. I also tried 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=intel" and ran sudo update-grub. Just got the same result of terminal after reboot.

In the terminal, If I try
sudo service gdm stop
and 
sudo service gdm start

it would give me a Black screen and then dead! Only power button works.

In the logfile, I still found this error info:
(EE) intel(0): No kernel modesetting driver detected.

BTW, I have to change the /etc/default/grub
back to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"

or else, It will Black and dead a few mins later even in the text mode.

:confused:

---

### Post by C.S.Cameron on 2010-10-26
Have 6you checked the MD5SUM of your iso?

---

### Post by Hooman on 2010-10-27
> **C.S.Cameron said:**
> Have 6you checked the MD5SUM of your iso?

Checked. It's same as the release site(1b9df87e588451d2ca4643a036020410). And the live cd mode works fine except the sound.

---

### Post by Hooman on 2010-10-28
Should I submit a bug for it?

---

### Post by Hooman on 2010-10-29
Is there anything I can do to resolve this problem?

---

### Post by fbjftw on 2010-12-18
Hi Hooman-

Have you found a solution to this problem?  I'm also interested, as I plan to buy a x201i and install ubuntu.

I ran across this page at lenovo that may be of help:
[INDENT][http://forums.lenovo.com/t5/Linux-Discussion-Knowledge-Base/Configuring-Video-on-X201i-running-Ubuntu/ta-p/313720](http://forums.lenovo.com/t5/Linux-Discussion-Knowledge-Base/Configuring-Video-on-X201i-running-Ubuntu/ta-p/313720)
[/INDENT]E

---

