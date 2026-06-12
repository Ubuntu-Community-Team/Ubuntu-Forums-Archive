---
title: "Need advice on reverting back to XP"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by geoff4376 on 2010-08-30
I have an old Dell Optiplex gx260 that has 10.04 already installed.  My brother needs a computer that has windows for reasons I won't question.  The problem is, I've heard that it isn't just as simple as booting from the XP install cd and reformatting the drive.  Do I need to somehow remove grub first?  Any advice would be helpful.



P.S.  I did search around a lot on google first, but all I found were conflicting answers, so I figured I would ask the experts (you guys).

---

### Post by an0dos on 2010-08-30
> **geoff4376 said:**
> I have an old Dell Optiplex gx260 that has 10.04 already installed.  My brother needs a computer that has windows for reasons I won't question.  The problem is, I've heard that it isn't just as simple as booting from the XP install cd and reformatting the drive.  Do I need to somehow remove grub first?  Any advice would be helpful.



P.S.  I did search around a lot on google first, but all I found were conflicting answers, so I figured I would ask the experts (you guys).

Your main problem will be drivers, which you can download from dell's support site. Otherwise, the windows install disk will completely remove ubuntu and grub.

---

### Post by BrockStrongo on 2010-08-30
I ran into a problem similar to this but involving reinstalling vista.
I had troubles getting grub completely removed from an ubuntu desktop. The only way I could get the hdd to format and completely remove all instances of grub was to hook it up to an existing windows machine and format it from there.

By the way, I am by no means an expert, just speaking from experience

---

### Post by Sef on 2010-08-31
> Your main problem will be drivers, which you can download from dell's support site. Otherwise, the windows install disk will completely remove ubuntu and grub.


As long as your internet works or you can get it to work, there should be no problem.

---

### Post by BrandyBear on 2010-08-31
i Ran into this problem a few monthes ago luckily i have a toshiba L300D satellite series and it came with a windows 7 Recovery disk so if you have a friend w/ a recovery disk enter the disk turn the computer off with the live CD in the disk tray like ubuntu it will Boot a 'Ramdisk Image' then follow instuctions from their

---

### Post by an0dos on 2010-08-31
If you do have problems with grub, you can enter the windows xp recovery console via the install disc and type in 'fixmbr'. [see here]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true") This will basically remove any changes grub made to the master boot record.

---

