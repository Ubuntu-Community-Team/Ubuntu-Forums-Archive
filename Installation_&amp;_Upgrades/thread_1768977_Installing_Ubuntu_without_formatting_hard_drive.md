---
title: "Installing Ubuntu without formatting hard drive"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by pcristian43 on 2011-05-27
OK everyone, so basically what I am trying to do is have Ubuntu as main operating system while not having to reformat my hard drive. I am currently using Windows 7, I tried to install Ubuntu from the Windows environment, using the installer version but it gives me a GRUB error and can't boot if I try to restart my PC and pick it as the OS to run. It would be cool if anyone knows a way around this problem, or at least how to install the OS without removing any files besides the Windows OS.

---

### Post by Hedgehog1 on 2011-05-27
For all intents and purposes, you cannot effectively install Linux in partitions are formatted in FAT, FAT32 or NTFS (the Windows' formats).

You can use the NTFS partitions for data storage, and the OS does eventually load the tools to read and write to FAT, FAT32 or NTFS partitions.  But at boot time, the partition needs to be ext2/3/4.

I am guessing you want to avoid formatting because you don't have a place to backup your data before loading Ubuntu?

There are some ways to get Ubuntu installed and you data moved, but in the end you really should backup your data to an external hard drive or CD/DVDs from time to time so recovery is possible should you drive ever fail (they all do fail eventually).

If you would like more detail guidance on installing Ubuntu, please do the following so we can determine the specifics about your PC:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

