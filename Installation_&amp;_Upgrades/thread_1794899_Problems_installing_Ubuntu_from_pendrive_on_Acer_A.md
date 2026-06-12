---
title: "Problems installing Ubuntu from pendrive on Acer Aspire One D260"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by Poletko on 2011-07-01
Hello. Please help me! I am having a problem installing Ubunbtu on my Acer Aspire One D260 (with Windows7 on it). I do have a pendrive with the correct installation files (used UNetbootin to create it). It works on my friends Assus. I have made a change in BIOS, changed to boot from my pendrive. Still after booting I get a black screen with this written on it:

Intel(r)PineView PCI Accelerated SVGA BIOS
Build Number: 1818 PC 14.34  06/19/2009  01:29:40
DECOMPILATION OR DISASSEMBLY PROHIBITED
COPYRIGHT (C) 2000-2003 Intel Corp. All Rights Reserved

-

"-" is flashing
I can imagine that the solution might be very simple but I am no "computer person". I would just like it to work. 
Did anyone have a similar problem? Could you please help?
I will be happy to hear from you.
Greetings!

---

### Post by mörgæs on 2011-07-02
For how long did you wait, while the underscore was flashing?

---

### Post by MazzSTM on 2013-02-03
Hi

I've got exactly the same issue today, a couple of year later than the original post, with Lubuntu and Aspire One D260.
Before going into black screen with:

Intel(r)PineView PCI Accelerated SVGA BIOS
Build Number: 1818 PC 14.34 06/19/2009 01:29:40
DECOMPILATION OR DISASSEMBLY PROHIBITED
COPYRIGHT (C) 2000-2003 Intel Corp. All Rights Reserved

it shows very quickly 
SYSLINK 4.03.(+something I'm not able to read as it is very fast)...

I waited a long with "-" blinking (more than an hour)

The USB pendrive works perfectly in my Dell laptop. Here I boot with no issues, no messages and very fast.

Any suggestion?

Thanks

Mazz

---

### Post by mörgæs on 2013-02-03
There could be several explanations. First, have you tried the alternate ISO?

---

### Post by MazzSTM on 2013-02-04
I've tried with 2 different ISOs, same problem.

Any other suggestion?

Mazz

---

### Post by mörgæs on 2013-02-04
No, but I have the same suggestion once more: Please try the alternate ISO and post the results.

Also, have you tried simply to push 'enter' at the underscore screen?

---

### Post by MazzSTM on 2013-02-04
I've done alternate ISO trial: same issue, exactly the same.

and, yes, press enter (and a thousand of other keys...), no effect, system is blocked. No way, the only way to get out is to press power supply and restart.

I'm still blocked.

Mazz

---

### Post by mörgæs on 2013-02-05
If you are talking of *the* (not *an*) [alternate ISO]("http://releases.ubuntu.com/precise/ubuntu-12.04.1-alternate-i386.iso") and it still doesn't work, it's a bug which needs to be fixed.

If you could please try the development version (13.04) and post your results in the corresponding [forum]("http://ubuntuforums.org/forumdisplay.php?f=427") then people there can help you with creating a bug report. This is the best way to get in touch with the developers.

---

### Post by MazzSTM on 2013-02-05
Ok,it was the alternate iso, this one: lubuntu-12.10-alternate-i386.
I try with 13.04.

thanks

---

### Post by MazzSTM on 2013-02-06
Just for info: I have solved the issue, that doesn't depend on OS release or version, but only how the BIOS lists the USB memory stick: the first stick I've used was list as FDD (and it doesn't boot from there), a second one il list as a hard drive (HDD) and it works.
Well I don't know the two memory sticks are seen by BIOS in a different way, but my issue is solved.

Mazz

---

### Post by mörgæs on 2013-02-07
That makes no sense to me, but anyway: Good to hear that it works. Please mark the thread 'solved'.

---

