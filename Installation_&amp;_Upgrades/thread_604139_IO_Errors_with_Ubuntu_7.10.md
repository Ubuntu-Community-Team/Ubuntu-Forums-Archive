---
title: "I/O Errors with Ubuntu 7.10"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by working_night_owl on 2007-11-05
I downloaded a mirror off the Ubuntu website for Ubuntu 7.10 and had the .iso file burnt to a disc. I then boot from the disc and get the start up screen for Ubuntu with the different options. I choose the "start up and Install" option so that I can install it to my computer. It loads the kernel and the Ubuntu logo appears for about a minute as it gets ready to start up Ubuntu. The screen then goes blank and the same two errors appear on the screen. The numbers at the beginning are different each time but the error codes are still the same:

[229.778171]  I/O error on device fd0, logical block0
[267.817808]  I/O error on device fd0, logical block0

It proceeds to load up the rest of the disk just fine with "OK" next to each start up process. Then the brown background appears and that is as far as it will go. I waited 15 minutes with no change. Is this because there is something wrong with the disc or is it because my computer is not compatible with the disc? Any help would be appreciated. Thanks.

---

### Post by Agabus on 2007-11-05
yeah I'm having what sounds like a very similar issue, however my install CDs were the official Ubuntu ones that were sent to me, so I gather it's not an issue related to an erroneously burnt disk.

fd0 I believe is the symbol for a floppy-disk drive? And since my computer doesn't have a floppy drive, perhaps the Ubuntu installer is probing for it, not finding it, and then becoming stuck.

does your computer have a floppy-drive?

can anyone help?

---

### Post by working_night_owl on 2007-11-06
My computer doesn't have a floppy drive so I don't understand why it would search for it.

---

### Post by yogeshmk on 2007-11-06
We're in the same boat! I'm striggling with issue from past 2/3 days.

My PC's floppy drive has been disconnected. and I see installation getting stuck at the exact same point as you said.

I have tried with both desktop installation CD and Alternate CD, but although error messages are different, they freeze at the same point. Desktop installation CD gives the error what you've reorted and alternate CD installation freezes at around 84% while searching for CD-ROM hardware saying

'loading 'IDE-floppy module' for 'Linux ide-floppr drive' I've waited for 15 mins here but installation did not proceed. I think both are symptoms of the same issue.

I'm looking for any help on this.

P.S. I have verified that this issue is not there with Ubuntu 6.06 installation CD.
cheers!

---

### Post by yogeshmk on 2007-11-06
Further to my post above, I am sure that there is no problem with the CDs, I've verified the MD5SUMs with the one's that are published.

also at shortly after the begining in text mode installation, I see a message
"[..]  '/sbin/modprob' abnormal exit"

--

---

