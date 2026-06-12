---
title: "Fresh install karmic OVER jaunty"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by smCw6GNakQn300£ on 2009-10-22
Hi folks,

First of all apologies - I know there are a TON of threads on this subject, but I couldn't find one that answers my questions and puts my mind at ease...

I currently use a laptop from work, which I have dual-booting between Windows 7 and Jaunty. I use Windows 7 for work.

Obviously, I want to move to Karmic when it's officially released, but I would like to perform a fresh install (to make use of all the new features - ext4 etc.)

My question is, using the live CD installer, can I simply tell it to perform a clean install, but simply to REPLACE/OVERWRITE the current jaunty install?
Is it as easy as selecting the same partitions during install?

Obviously, one of my primary concerns is the Win 7 partition (for work), so would the above leave this alone? (provided I choose the correct install partition!!)

Also, what about GRUB - will it recognise that Windows is present and build-in a boot option for that too?

Thanks.

---

### Post by raprap30 on 2009-10-22
Yeah, Grub 2, which is included in Karmic, will detect you Fail(windows)7 install, however, it is expected to fully format the jaunty partition, and THEN install karmic over it.  So YES, it will leave the Win 7 partition alone.

---

### Post by smCw6GNakQn300£ on 2009-10-22
Ok, thanks.

Sounds as straight-forward as I'd hoped.

:-)

---

### Post by megamanexent on 2009-10-23
> **BRY said:**
> Hi folks,

First of all apologies - I know there are a TON of threads on this subject, but I couldn't find one that answers my questions and puts my mind at ease...

I currently use a laptop from work, which I have dual-booting between Windows 7 and Jaunty. I use Windows 7 for work.

Obviously, I want to move to Karmic when it's officially released, but I would like to perform a fresh install (to make use of all the new features - ext4 etc.)

My question is, using the live CD installer, can I simply tell it to perform a clean install, but simply to REPLACE/OVERWRITE the current jaunty install?
Is it as easy as selecting the same partitions during install?

Obviously, one of my primary concerns is the Win 7 partition (for work), so would the above leave this alone? (provided I choose the correct install partition!!)

Also, what about GRUB - will it recognise that Windows is present and build-in a boot option for that too?

Thanks.


I have a similar set-up as BRY, except instead of Windows 7, I have windows XP. My question is, given that Karmic contains grub2, will i be able to do a fresh install of Karmic in a new partition and still boot into Windows AND Jaunty installs? Jaunty currently has grub-legacy installed.  Will there be any conflicts with grub2 and grub-legacy?

The ideal set-up would be Karmic/grub2 over-writes the MBR with grub2 and finds both the windows & Jaunty partitions and boots into them. I really dont want to upgrade grub-legacy to grub2 seperatly. If I have to though, I will.

---

### Post by ikisham on 2009-10-23
No problem, mate. Just in case grub2 doesn't pick your XP, it'll be as easy as with grub legacy to edit it.
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by megamanexent on 2009-10-23
LOL, you know I found this thread and totally miss the "non grub2 Ubuntu OS" part. I was really trying to learn how to edit grub2 more than finding out if Jaunty would work with grub2. Thank you though.

---

