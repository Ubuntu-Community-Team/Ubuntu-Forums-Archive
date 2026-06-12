---
title: "I/O error?"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2008-05-11
When I boot from the hardy heron live disc, it says something like:

I/O error in device fd1 logical block 0

It hangs like that for about 30 seconds, then it boots up into ubuntu live.

Is it something bad? Can I fix it?

---

### Post by Aearenda on 2008-05-11
fd1 sounds like a diskette drive - but you would have to have two to get fd1 showing up, rather than fd0. Anyway, is there a diskette in the drive?

---

### Post by Fzang on 2008-05-11
No, the only thing is a ubuntu live CD

Now it just said:


Buffer I/O error on device fd1, logical block 0
Buffer I/O error on device fd1, logical block 0
Buffer I/O error on device fd0, logical block 0
Buffer I/O error on device fd0, logical block 0
Buffer I/O error on device fd1, logical block 0
Buffer I/O error on device fd1, logical block 0
Buffer I/O error on device fd1, logical block 0

And I turned off the computer. After that I rebooted and it didn't say anything, but booted the CD

What's going on?

---

### Post by Aearenda on 2008-05-11
A ghost in the machine!

Does your BIOS have an option to disable floppy drives? Maybe that will banish it.

---

### Post by Fzang on 2008-05-11
There's no floppy drive settings, hence my computer doesn't even have a floppy drive

Could it be something wrong with the ubuntu CD? I ran the "check cd" from the boot menu and it checked...went black... came up with 
"Buffer I/O error on device fd1, logical block 0"

I'll try make a new one with a brand new CD... the old CD has been used for ubuntu, dreamlinux, winXP and ubuntu again - Could I have killed the poor thing?

---

### Post by Aearenda on 2008-05-11
Weird! It sounds like your computer is confusing the CD drive with a floppy drive.

Anyway, yes, you could try a new live CD, or the Alternate installation CD. 
Also how much RAM in your machine? See the start of [http://ubuntuforums.org/showthread.php?t=609319](http://ubuntuforums.org/showthread.php?t=609319).

It happened in [http://www.justlookdifferent.com/2008/04/29/ubuntu-804-64-bit-lts-desktop-edition-review/](http://www.justlookdifferent.com/2008/04/29/ubuntu-804-64-bit-lts-desktop-edition-review/) but installation proceeds.

---

### Post by Fzang on 2008-05-11
EDIT:

I went into BIOS and it says "Extended memory: 1790 mb"

Is that my memory?

---

### Post by DBrocks on 2008-05-11
Hmmm I believe I had something like that happen to me once. I opened my computer, and found my floppy drive to be unplugged from power. Try making sure it is fully plugged in. Also, try disconnecting the IDE or Sata cable, and the power cable, that way it won't be able to see the floppy drive

---

### Post by Fzang on 2008-05-11
It doesn't have a floppy drive, and it never had >_>?

---

### Post by Aearenda on 2008-05-11
Usually it will say how much RAM (extended plus basic) you have on the BIOS screen as it starts up. Anyway, you have plenty, so it's not that.

How did you go with the new CD?

---

### Post by Aearenda on 2008-05-12
Another idea: there is a kernel parameter 'floppy=off' that I just came across in another thread - perhaps it will suppress this issue. Here's how to test it:

At boot time, press ESC to enter the Grub menu.
Use <up>/<down> if necessary to select the Ubuntu entry.
Press 'e' to edit.
Use the <up>/<down> keys to select the kernel line.
Press 'e' to edit
Go to the end of the line and add a space and 'floppy=off' 
Press <enter>
Press <b> to boot.

This can be made permanent if it works.

---

### Post by bigken on 2008-05-12
try shorting the cmos battery to reset the bios sounds like a bad checksum error

---

### Post by housam on 2008-05-12
> **Fzang said:**
> 
I'll try make a new one with a brand new CD... the old CD has been used for ubuntu, dreamlinux, winXP and ubuntu again - Could I have killed the poor thing?

Try to burn the new CD at slow speed as 2x or 4x . this 'll prevent burning errors.

---

