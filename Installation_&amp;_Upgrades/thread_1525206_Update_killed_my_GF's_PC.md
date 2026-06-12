---
title: "Update killed my GF's PC"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by MR.T on 2010-07-06
My girlfriend has a computer that runs Ubuntu (it was her brother-in-law's doing not mine). Unfortunately I do not know what version it is, but it is either 8.? or 9.?. Recently she did an update and now the desktop wont load. It is all just console stuff and I think she said there was some error about fsck. I have not had a chance to see what the problem is, but I want to be prepared before I go there. What should I take with me? Does Ubuntu have some sort of recovery/restore option? Will the latest version still allow me to fix her version, or do I need her specific release?

---

### Post by WinRiddance on 2010-07-06
Not meaning to be insensitive to the problem at hand ... but you provided pretty much ZERO information that anyone can make any use of. Maybe it would help to divide your required solution(s) into a two step process, even if that means during two separate days ....

Step 1:  First find out as much actual information about the hardware as you can, as well as any important information from your girlfriend regarding the Ubuntu version, type of software she was using (OpenOffice version could be helpful), and anything else that might help.

Step 2: Then come back to the forum, armed with information that can actually be used to provide some assistance. It's next to impossible to work completely blind-folded you know ....

---

### Post by gradinaruvasile on 2010-07-06
fsck... Thats not good.
Log in text mode with the recovery option.
First, find out the boot partition (the " / " is "space/space":

```
mount | grep " / "| cut -d ' ' -f1
```
The return will be something like (not necessarily)

/dev/sda1

Then check that partition:

```
fsck -f /dev/sda1
```

Again, the "/dev/sda1" is what you got with the first command.

If it works, after the fsck is finished, type "reboot", then press enter.

---

### Post by pricetech on 2010-07-06
You should be able to boot to a live CD no matter which version you use, but unless you are going there just to salvage her data, then yes we need a lot more information.  DON'T attempt a repair until you know what you're doing.

---

