---
title: "Toshiba NB200  Ubuntu 10.10 upgrade problem slow erratic reboots"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by pete2222 on 2010-10-05
[COLOR=black][FONT=Arial]I upgraded from 10.04 to 10.10 and found that it took ages to restart or start up, and this seemed to vary.[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]Has anyone else had this problem. Could it be associated with the way I upgraded? Is it better to do a fresh wipe/install? I have gone back to 10.04 for now and it works great, but would like to use 10.10 if I could get working as well. [/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]Please tell me if you are running Ubuntu 10.10 well on a Toshiba NB200 netbook .[/FONT][/COLOR]

---

### Post by mörgæs on 2010-10-05
Toshibas can be tricky - they are well-known in the forum... If you have a working 10.04, why not stick to it? 

However, if you want to experiment with 10.10, here is some advice:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Just remember that Ubuntus (like Windows) always needs a few months after release to be really stable.

---

### Post by empoulator on 2010-10-06
I got a similar problem. Yesterday, for the first time, I was proposed to update Ubuntu 10.10. 

Since then, I cannot get the graphical interface working... I just spent 5 frustrating hours trying to make it work again with no result. 

I got a new computer recently and installed Ubuntu 10.10 because it made everything work smoothly from the beginning. This was not the case with Ubuntu 9. 

> **mörgæs said:**
> Toshibas can be tricky - they are well-known in the forum... If you have a working 10.04, why not stick to it? 

However, if you want to experiment with 10.10, here is some advice:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Just remember that Ubuntus (like Windows) always needs a few months after release to be really stable.

---

### Post by grugef on 2010-10-10
I had the same problem, downloaded it today and spent all evening to try to install it, without success. I'm a newby, it's the first time I use linux, but the problems I experienced don't seem to be my fault.

I began to install in the afternoon, and after some hours of black screen a few command lines scrolled down, followed by the ubuntu logo with the red dots. I had dinner, washed dishes and wore pijama, and the logo was still there, but a red dot became white..
I went to sleep, got up in the morning and had breakfast, and there were two white dots, but nothing else.
Time passed, I celebrated Christmas and New Year's Day, but still no news from my netbook.
After the time a turtle spends to circumnavigate the Earth walking backwards I decided to shut the pc down and download ubuntu 10.04.
Tomorrow i will try with that version, hoping in more luck.
I'll let you know..

---

### Post by pete2222 on 2010-10-10
> **grugef said:**
> I had the same problem, downloaded it today and spent all evening to try to install it, without success. I'm a newby, it's the first time I use linux, but the problems I experienced don't seem to be my fault.

I began to install in the afternoon, and after some hours of black screen a few command lines scrolled down, followed by the ubuntu logo with the red dots. I had dinner, washed dishes and wore pijama, and the logo was still there, but a red dot became white..
I went to sleep, got up in the morning and had breakfast, and there were two white dots, but nothing else.
Time passed, I celebrated Christmas and New Year's Day, but still no news from my netbook.
After the time a turtle spends to circumnavigate the Earth walking backwards I decided to shut the pc down and download ubuntu 10.04.
Tomorrow i will try with that version, hoping in more luck.
I'll let you know..

10.04 works great on a toshiba NB200. There are two quite simple things you need to do though. The first is  is to fix the sound, the second is to make the bootup speed normal. Here is the link to the sound fix

[http://ubuntuforums.org/showthread.php?t=1455705&highlight=10.04+sound+NB200](http://ubuntuforums.org/showthread.php?t=1455705&highlight=10.04+sound+NB200)

---

### Post by StealthCP on 2010-10-14
Ok guys, I got three of these today, and I reckon this could be a kernel issue.

In the installer, you might notice it going slowly.  On the boot splash, you may notice even the dots stop changing in sequence.

You might notice holding a key on the keyboard, or moving the touchpad continuously, solves this problem.  Basically, if there is user input there, it continues to tick.

Could this be an issue with the Atom Processor?  Can anyone else confirm this behaviour on other Atom based machines during these times?  It doesn't happen when you are in your desktop environment, but does in the installer, on bootsplash, and even the bootloader can fail to load up if I'm not tapping keys constantly.

I'm going to run a few more tests, I'll report back on anything I know.

EDIT: A temporary fix seems to be changing the SATA mode in the BIOS from AHCI to compatibility.

---

### Post by waveskiJohn on 2010-10-18
Thanks StealthCP - setting the SATA to compatibility and waggling a finger over the touchpad works for me (hadn't thought of trying that), as does booting up with the previous kernel version.

---

### Post by andy258 on 2010-10-31
Hi,
I had random boot delay issues, not sure if they're the same, my unit is up and running in around 25 seconds. Used this fix, can't remember who posted it now, but it worked a treat for me:

/etc/grub.d/10_linux
add nohz=off to end of line:

EOF
  fi
  cat << EOF
 linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args} nohz=off

then update grub:
sudo update-grub

---

### Post by netmonky on 2010-10-31
I also have a nb200 and upgraded to 10.10 today. As all users above, when i boot using 2.6.35-23 i have to hold the enter key to keep it "ticking on". If i boot 10.10. with 2.6.32.35 all works as expected so I suspect this is a kernel issue :-(. 

Any other workarounds would be helpful :-)

---

### Post by thnurg on 2010-11-03
I found this today. It appears to have worked for 10.10 on my NB200.

[http://www.linlap.com/wiki/toshiba+nb200](http://www.linlap.com/wiki/toshiba+nb200)

Add nohz=off to your kernel options as mentioned.

---

### Post by andy258 on 2010-11-03
Remembered where I found it:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205")

---

### Post by GapInTheClouds on 2011-03-19
Excellent! The nohz=off trick worked a treat for my NB200. Thanks for that!

I got fed up of wiggling the mouse to make it boot, so I was just using the old kernel, but now I can use the shiny new kernel :D. Thanks again.

---

