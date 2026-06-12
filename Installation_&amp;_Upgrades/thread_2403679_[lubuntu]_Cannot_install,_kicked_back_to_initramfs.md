---
title: "[lubuntu] Cannot install, kicked back to initramfs"
date: 2018-10-14
forum: Installation &amp; Upgrades
---

### Post by mikezuccaberg on 2018-10-14
Hi all,

I have an older HP Stream netbook and am trying to install Lubuntu.  I am using an app called UNetbootin with the latest .iso of 64 bit Lubuntu.  Whenever I try to either install it OR just run it off of the flash drive, it quits halfway through and goes to a command line that starts with (initrafms).

Most of the threads I have found via searching indicate that I should type fsck and this or that command, but fsck is not recognized by initrafms on my machine (I forget the exact error message, "not recognized" sounds close).

Sorry if this is a dumb question, I am not a computer expert by any means!

Edit:  Things I have tried since posting include...

 - chose the non-UEFI option for booting from USB, which took me to a different install screen.  Still didn't work though;
 - Did the "nomodeset" thing, no dice;
- Safe Boot is not enabled in my BIOS;
- Tried the default USB boot maker in Mint rather than UNetbootin.

---

### Post by mikezuccaberg on 2018-10-15
I cannot boot other distributions either - it always hangs or something.  I suppose this points to a BIOS issue, but I have tried all the possible combinations of legacy vs. UEFI on/off and secure boot on/off.  I am puzzled.

---

### Post by mikezuccaberg on 2018-10-16
I got it to boot one time and then I didn't set the partitions properly (a noob guide for that would help) and it froze.  I cannot replicate the boot for some reason.

Say what you will about Windows, at least it's plug-n-play.  Guess I'm pretty much talking to myself here.

---

### Post by Bashing-om on 2018-10-16
mikezuccaberg; Hello - Welcome to the forum .

Naw: "Guess I'm pretty much talking to myself here."
Just not enough info to make a recommendation - yet.

Does the liveUSB boot in another system ?
Have you verified the USB's integrity ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

We get a firm foundation 
[INDENT][INDENT]and then push
[/INDENT][/INDENT]

---

### Post by mikezuccaberg on 2018-10-18
Somehow the problem was related to either the ISO or how it was written to the flash drive.  After much aggravation, I simply instructed Unetbootin to download Lubuntu from its sources (rather than using the ISO I had on disk) and load it on the flash drive, which worked on the first try.  Odd.

---

### Post by Bashing-om on 2018-10-18
mikezuccaberg: Great !

sometimes a fresh start works wonders :)

[INDENT]a Firm foundation
[/INDENT]

---

