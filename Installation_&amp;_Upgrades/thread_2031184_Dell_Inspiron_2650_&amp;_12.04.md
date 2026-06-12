---
title: "Dell Inspiron 2650 &amp; 12.04"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by Robbobden on 2012-07-21
This thread is closed:  [http://ubuntuforums.org/showthread.php?t=1792335&highlight=2650](http://ubuntuforums.org/showthread.php?t=1792335&highlight=2650)  

So, I started a new one here.    This Inspiron 2650 has the P4 Mobile 1.6G and 512M memory.   I tried Ubuntu 12.04, Mint 13 and Arch.   The LiveCDs hang on bootup unless I add acpi=off to boot parameters.    12.04 is installed and loaded up with what I use.   Here's the problem with acpi=off:   The CPU runs at max virtually all the time.    I see this when I run the command:   'top'   in terminal.   (Note:  I went back and loaded the 12.04 LiveCD up and in terminal, ran the 'top' command.   CPU usage is 100% just running the LiveCD).     Ok, so I found a thread somewhere suggesting use of  pci=noacpi  as a boot parameter instead of acpi=off.   Well, that solved the high CPU usage.   (And the PC will power down with software command too.)  It's down to under 8-10 percent now on average.   BUT, there's no touch pad or keyboard.   Both inoperative !    They both work using the LiveCD with just pci=noacpi, but not after installing to hard drive.   Figure that out.   There's more.    If I physically remove the battery (which holds zero charge anyway),  and still using pci=noacpi boot parameter, mouse pad and keyboard work great.   CPU usage still normal.  What does that mean ?   If I get a new battery at $41. would I expect the touch pad and keyboard to work then ?   

BTW, Linux Puppy 5.3 boots up right out of the box.   I'm checking that out now but at first look,  security doesn't look too good.   The command line is #:   No root password ?

RDL

---

