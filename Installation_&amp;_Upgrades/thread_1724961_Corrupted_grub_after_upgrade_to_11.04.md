---
title: "Corrupted grub after upgrade to 11.04"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by xilod on 2011-04-09
Hello everyone! 

Yesterday all my troubles seemed so far away, because I've been using working system with Windows 7 & Ubuntu 10.10, but last night I decided to update to 11.04 from update manager. So, when upgrade was done, I rebooted and saw something like this:
"grub_env_export not found
grub rescue > "

Do I have a problem with MBR? Will it help, if I load from Ubuntu live cd and try to reinstall grub? If so, how can I do it correctly(I'm quite new to Ubuntu and Linux)?

Thanx a lot

---

### Post by Hedgehog1 on 2011-04-10
Lets see if we can help :p

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


***The Hedge***

:KS

---

### Post by xilod on 2011-04-10
Thank you, but I've already found a solution, it was as follows:

Booted from Ubuntu Live CD and reinstalled GRUB(and wiped out 32d sector where GRUB saw FlexNet) then I had GRUB worked, but Win 7 couldn't load. So I booted from CD with Win 7 distr, where I choose Repair System->Command Line-> Bootrec.exe /FixBoot

And now everything works!

---

