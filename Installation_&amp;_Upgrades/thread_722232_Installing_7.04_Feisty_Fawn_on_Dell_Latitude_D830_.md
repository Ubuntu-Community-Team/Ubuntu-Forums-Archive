---
title: "Installing 7.04 Feisty Fawn on Dell Latitude D830 with nVidia Quadro NVS 140M"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2008-03-12
We found these other threads indicating to install on this system via the alternate install CD, and first install the command line system. We did so, but the boot process hangs at this point:

* Starting deferred execution scheduler atd                  [OK]
* Starting periodic command scheduler crond              [OK]
* Running local boot script (/etc/rc.local)                      [OK]

blinking cursor under last OK

The referring threads were:

 TTY Error + Dell Latitude Notebook
[http://ubuntuforums.org/showthread.php?t=524719](http://ubuntuforums.org/showthread.php?t=524719)
(Which was the first error, when trying to boot the GUI installer / normal CD vs alternate)

X won't start: Latitude D830 WUXGA 256MB NVIDIA® Quadro NVS 140M
[http://ubuntuforums.org/showthread.php?t=497049](http://ubuntuforums.org/showthread.php?t=497049)

I find no references to trouble experienced booting the command line system.

I am suspecting that /etc/rc.local finished since it has OK after it. What would the next thing be that it should be trying?

Thanks in Advance! :-)

---

### Post by mdlueck on 2008-03-12
Solved!

We reinstalled again from the alternate CD, command line system. Same partitions, just reset the mount points and flagged all partitions to be re-formatted.

And up it came!

The next line should have been the login prompt. I have not a clue why it was getting stuck right there, but glad it is not any more.

---

