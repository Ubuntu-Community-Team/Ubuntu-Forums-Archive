---
title: "Ready to throw in the towel"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by darkbrewer on 2010-08-30
I 've been trying to install ubuntu 10.04 on one of my computers for about 3 weeks and just when i think i solved the issue and reboot the computer i get this message:

                  GNU Grub version 1.98-1ubuntu7

Minimal BASH-like line editing is supported.For the first word,TAB lists possible command completions.Anywhere else TAB lists possible device or file completions.

grub>_ 

NOW can anyone explain or tell me what the heck am I suppose to do?
why do they make this process soooo hard for people who don't have a degree in programming.I so fed up now it's ridiculious,maybe i should sell my soul back to Microsoft and Bill Gates in order to get an OS to work on my computer!!! Can someone help me out .:-({|=

---

### Post by buntunub on 2010-08-30
It sounds like something either went horribly wrong with your install or your CD burn.

Please provide more detail. 

1. Does this happen after you have successfully done a livecd install?... Meaning, did you get the message that the install succeeded and to reboot?

2. If you have not installed and are getting this message from the livecd boot process, did you:
A) check the CD for defects after you burnt it?
B) download the correct version for your computer (32bit or 64bit)?

---

### Post by v1ad on 2010-08-30
if installing from usb, sometimes it uses the usb as the boot directory. plugin the usb and boot. and once you are in do.
```

sudo apt-get --purge remove grub grub2

sudo apt-get install grub2

update grub2


```

have it happen to me often.

---

### Post by kansasnoob on 2010-08-30
> **darkbrewer said:**
> I 've been trying to install ubuntu 10.04 on one of my computers for about 3 weeks and just when i think i solved the issue and reboot the computer i get this message:

                  GNU Grub version 1.98-1ubuntu7

Minimal BASH-like line editing is supported.For the first word,TAB lists possible command completions.Anywhere else TAB lists possible device or file completions.

grub>_ 

NOW can anyone explain or tell me what the heck am I suppose to do?
why do they make this process soooo hard for people who don't have a degree in programming.I so fed up now it's ridiculious,maybe i should sell my soul back to Microsoft and Bill Gates in order to get an OS to work on my computer!!! Can someone help me out .:-({|=

How many operating systems?

Does this happen only after booting into a Windows OS?

There are still a number of issues with grub2:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

We need a much clearer description of the problem, and possibly the output of the Boot Info script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-08-30
> **v1ad said:**
> if installing from usb, sometimes it uses the usb as the boot directory. plugin the usb and boot. and once you are in do.
```

sudo apt-get --purge remove grub grub2

sudo apt-get install grub2

update grub2


```

have it happen to me often.

There's a huge degree of nonsense to that. If the package "grub" is NOT installed then the "stacked" command should make purging "grub2" impossible, but regardless the package "grub2" is a "dummy package".

The proper package name is "grub-pc". And if you have mixed legacy grub and grub 2 files in /boot/grub you will continue to have trouble forever!

Look here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

You'll notice in appendix #2 I talk about reinstalling grub2 :D

---

### Post by rpaco on 2010-09-18
I have exactly the same problem, brand new hard disk in my laptop, the  old one having been damaged by overheating. Have put it back in (after  fsck-ing it) to type this.

In my case I am using the same CD with text version 10.04 that I have  already used successfully on both my and my neighbour's pcs and  previously on the old HD in this laptop. (the text version ISO has no  live Ubuntu session on it)
Whole process runs as expected until the "remove CD and reboot"  Then instead of the grub menu offering kernel versions one is left with a "grub>" prompt and notice about  a limited list of possible  commands, all of which are unknown and highly specialised. 
Running "boot" at the grub> prompt tells me there is no kernel loaded.

I have run the "Fix broken system" option thee times, re-installing Grub twice more to no effect whatsoever.

I can get a command line in /sda1 from the end of the recovery menu, would running fsck fix this?
I have the impression that either grub or the boot sector has not been written properly

---

### Post by rpaco on 2010-09-19
I tried what kansasnoob said above:

sudo apt-get --purge remove grub grub2
then re-installing it,
sudo apt-get install grub2 
update grub2
This made no difference the same problem remained.

Also from another thread I tried
sudo grub-mkconfig && update grub
Which ran nicely but has no effect on the problem.

Finally got a working system again on my new hard disk.
I used the expert mode in the recovery utility from the main CD menu  though it would have been better to just do a reinstall. This time I  selected "Use all and disk and LVM. Which forced a re partitioning of  the disk.
This then gave a different problem and I ended up after reboot with  prompt that said "grub rescue>"  No help at all no list of commands,  nothing. So I reinstalled again and this time not in expert mode and the  whole went like clockwork.

---

