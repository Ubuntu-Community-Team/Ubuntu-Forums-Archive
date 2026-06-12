---
title: "Unable to boot x86 live cd"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by Sewden on 2006-10-04
HI,

when my system boots from the live cd the main installation screen appears.  When i start the loading proccess the kernel loads 100% and then my sytem just reboots of it own accord.  Help anyone?

---

### Post by whizbaby on 2006-10-04
There are several possibilities:
- do you meet the requirements (at least 192 MB of RAM or so)?
if yes, you can
- burn the same image at a slower speed (2x -8x)
- burn the *alternate installation cd* and try with that (try this if you have less than 192 of RAM, too).
(some CDdrives don't like some particular CDs) 
Any changes?

---

### Post by Sewden on 2006-10-04
Have 512mb RAM and am using v6.06 sent through post.  Also downloaded and burnt knoppix iso and tried that.  Exactly the same problem occured, it just rebooted the system.  Must be a problem with my system.  But what?

---

### Post by Sewden on 2006-10-04
Also what's different about the alternate cd?

---

### Post by whizbaby on 2006-10-04
> **Sewden said:**
> Must be a problem with my system.
Just can guess ... you got SATA hard drive?
Does putting the HD before the CD in BIOS boot menu change anything?

The alternate CD generally has more options (e.g. kernel to use) so more hardware is supported.

---

### Post by Sewden on 2006-10-04
Don't know what SATA is.  And, no, putting HD before CD in BIOS just makes it boot to HD.

---

### Post by Sewden on 2006-10-04
Oh you mean bus type.  No it's ATA.

---

### Post by Sewden on 2006-10-04
Will try the alternate cd.  Any other suggestions though?

---

### Post by whizbaby on 2006-10-04
> **Sewden said:**
> And, no, putting HD before CD in BIOS just makes it boot to HD.
Sorry, don't know why I thought you had it installed on HD (how would you without working cd).

:oops:

---

### Post by Sewden on 2006-10-05
Just tried the alternate iso burn with no joy.  Exactly the problem as previously mentioned.  Suggestions anyone?

---

### Post by whizbaby on 2006-10-05
You could try booting with the *noapic* option:
When the CD menu shows up hit F6 and put
noapic
before the final --
then <return> to boot.
EDIT:
I talked about the desktop CD, don't have the alternate here to check.

---

### Post by Sewden on 2006-10-05
Tried the boot with *noapic* option on both alternate and normal and still same problem.  Just scratching my head!?

---

### Post by whizbaby on 2006-10-05
Please give us a little information about your CPU and mainboard.

---

