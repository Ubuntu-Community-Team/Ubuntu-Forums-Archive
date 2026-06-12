---
title: "initramfs busybox 1.22.1"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by ahmedovic99 on 2017-07-22
Hi!
I suddenly shocked with this problem. And never used the computer a week ago.
Please find me the solve.

hp pavilion g6 1226-sx
Intel core i5-2430m, 2.4 giga hertz
hardisk 750 gb
memory DDR3 SDRAM 6gb


My regards.
[IMG]https://www.gulf-up.com/imagef-1500799177891-jpg.html[/IMG]
[IMG]https://www.gulf-up.com/imagef-1500799178492-jpg.html[/IMG]
[IMG]https://www.gulf-up.com/imagef-1500799179073-jpg.html[/IMG]

---

### Post by Bashing-om on 2017-07-22
ahmedovic99; Hello; Welcome to the forum ,

Your provided images are not useable. We need some other means to obtain info .
What are your system specs ?
Manufacturer ? Desktop or laptop ?
CPU ?
amount of ram installed ?
video chip ?

How far do you get in the boot process and what are the error messages that the system provides ?
Can you boot as far as the grub boot menu to try a recovery kernel to boot up ?

[INDENT][INDENT]help us to help you
[/INDENT][/INDENT]

---

### Post by ahmedovic99 on 2017-07-23
Done, please help :(

---

### Post by Bashing-om on 2017-07-23
ahmedovic99; OK - Not

All kinds of errors in regards to the 1st hard drive.
Undetermined at this time if all these errors are due to file system corruption or hardware failure .
At this point we take the system's advise and run a file system check on the partitions of that 1st hard drive.
So, show us what we are working with;
Booted from the liveDVD(USB) into the "try ubuntu" mode
 Post back - Between Code Tags -  the outputs of terminal commands :
```

sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
So we identify the target(s) for the file system check/repair.
Using this live mode we try not to make the situation any worse than it is .

[INDENT][INDENT]bad things can happen
[/INDENT][/INDENT]

---

### Post by ahmedovic99 on 2017-07-24
The same problem. OK, if I want to install windows 10 what are the steps 'from cd'. "I tried many times to install it but "initramfs" window still spears.

---

### Post by Bashing-om on 2017-07-24
ahmedovic99; Hey !

I can not advise about Windows - I have not done Windows in so many many years .

As to your current install of ubuntu - If you put some effort into following instructions - there is a good chance to find and correct the problem(s) .

[INDENT][INDENT]teach a man to fish
[/INDENT][/INDENT]

---

