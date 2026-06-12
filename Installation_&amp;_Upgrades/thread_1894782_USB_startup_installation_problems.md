---
title: "USB startup installation problems"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by Hadeda on 2011-12-13
USB startup installation problems

This issue is outstanding for over a year:
[http://ubuntuforums.org/showthread.php?t=1572817](http://ubuntuforums.org/showthread.php?t=1572817)

I created a new USB stick from a fresh 10.04.3 image.

Same message: "Boot Error" on a blank black screen.

Can a guru help me please? 

Many thanks

---

### Post by gordintoronto on 2011-12-13
More details, please. What do you mean by "a fresh 10.04.3 image"? Do you mean that you went to the Ubuntu web site and downloaded the Ubuntu 10.04.3 32-bit desktop ISO?

What program did you use to create the USB stick? I generally use Multisystem, even though it sometimes crashes my machine after it has finished what it was doing.

Finally, tell us about a specific machine which produced the "boot error" message: CPU, memory and video adapter. And confirm that you actually booted from the USB stick.

When a LiveCD/USB sometimes works and sometimes doesn't, it seems likely that you have the 64-bit version, which won't work on computers with 32-bit CPUs.

---

### Post by Hadeda on 2011-12-13
Thanks gordintoronto

>Do you mean that you went to the Ubuntu web site and downloaded the Ubuntu 10.04.3 32-bit desktop ISO?

YES

>What program did you use to create the USB stick?

Ubuntu's systen > administration  "Startup Disk Creator"


> confirm that you actually booted from the USB stick.

I confirm that the bios was set to boot first from the USB stick. 


>When a LiveCD/USB sometimes works and sometimes doesn't, it seems likely that you have the 64-bit version, which won't work on computers with 32-bit CPUs.

Is ubuntu-10.04.3-desktop-i386.iso the 32 bit version? That's the one I downloaded.

Hope that helps, gordintoronto

---

### Post by gordintoronto on 2011-12-13
You skipped the most important question.

I have tried to use Startup Disk Creator, and have never produced a useful flash drive with it. Perhaps I was missing something, but it was very easy to just move to another option.

---

### Post by Hadeda on 2011-12-14
Gord, 
Are you saying that there is a design flaw in the Startup Disk Creator for over a year now?

Surely, many people must have the same problem. 
If yes, how can this be escalated to Ubuntu's senior team for attention and an answer?


I am missing something. Can someone clear this up for me?

Thanks!

---

### Post by Hakunka-Matata on 2011-12-14
Since you are evidently using an Ubuntu system to create a liveCD/USB I suggest you download and use **unetbootin  **to install the downloaded .iso file to the CD/USB.  There are lots of programs out there dedicated to that task, but after doing this through 7 or 8 Releases, using various different installation programs, I've settled on **unetbootin **as the most reliable.

---

### Post by gordintoronto on 2011-12-14
> **Hadeda said:**
> Gord, 
Are you saying that there is a design flaw in the Startup Disk Creator for over a year now?

Surely, many people must have the same problem. 
If yes, how can this be escalated to Ubuntu's senior team for attention and an answer?


I am missing something. Can someone clear this up for me?

Thanks!

I'm just saying that it has never worked for me. Perhaps someone could file a bug, but the process is time-consuming.

---

### Post by Hadeda on 2011-12-22
Thanks. I have used unetbootin without a glitch.

However, there are 2 boxes which simply do not want to co-operate and continue to come up with the "boot error" message.

Have solved the issue by burning a CD instead. :)

---

### Post by darkod on 2011-12-22
Can it be that those two boxes were not actually booting from the usb and giving the error if there was no other device to boot from? But anyway, you solved it by using a cd. It seems booting from usb might have been the problem, not the actual usb stick.

For the record, I have used Startup Disk Creator and it has worked fine for me.

---

