---
title: "Won't boot after 12.04 to 14.04 upgrade"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by dtrumbell on 2014-08-22
I just upgraded from 12.04 to 14.04.  After the upgrade the machine rebooted fine.  The next time I rebooted, the machine didn't come back.  Can't ping it, can't SSH.  What's most bizarre is that I tried hooking it up to my TV with a displayport to HDMI adapter to see what's going on and no picture is displaying.  I did originally install 12.04 using the same setup to a TV a year or so ago.

Seems like a video problem?  Thoughts on how to fix this?

Thanks in advance,
David

---

### Post by mörgæs on 2014-08-23
How does it work in a live boot of 14.04.1?

---

### Post by dtrumbell on 2014-08-25
> **mörgæs said:**
> How does it work in a live boot of 14.04.1?

I tried hooking this up to a VGA monitor and that didn't work either.    Then, I tried the above with my 12.04 install disk, but that didn't work either.

Am I out of luck here?  What can I do to try to recover?

Any help here is appreciated.

Thanks,
David

---

### Post by dtrumbell on 2014-08-25
I figured this out.  After trying several permutations of monitors and ports, I opened up the machine and immediately noticed there was a graphics card installed in a PCIe slot.  I plugged a monitor into the display port on this and boom, had a picture.

Once I solved that, it was easy to see the issue.  During the boot sequence, it was complaining that it couldn't mount drives over sshfs, requiring user input.  I've now booted successfully into the command prompt.

Now to fix the sshfs issue, then go back to being headless..

Thanks for the help!

David

---

### Post by Bashing-om on 2014-08-25
dtrumbell; Hi !

Observations:
Does the liveDVD ( install disk) boot up in a different machine ?
Does the VGA monitor work when hooked up to a different machine ?
Does the different machine's monitor work when the monitor cables are switched ?

Double check that in bios you are setting the boot priority to the CD drive, IF indeed you can see the bios and bios's boot screen then it is certainly indicative that the monitor and cable are good.
Are you where you can hear the beep codes from bios when the system is started ? .. maybe research what the sequence implies ?

Else, maybe you are looking at hardware failure .

[INDENT][INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT][INDENT]a process in the making
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

