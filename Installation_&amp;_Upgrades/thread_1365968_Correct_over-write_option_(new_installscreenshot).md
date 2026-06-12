---
title: "Correct over-write option? (new install/screenshot)"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2009-12-27
Indulge me please on a simple question here... I want to put 9.10 on top of 8.04. Backup is done.

Which option is correct?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141419&d=1261970997[/IMG]

---

### Post by presence1960 on 2009-12-27
Choose the manual option then choose the 8.04 partition by right clicking on it and choosing Change. A window will open- you need to set parameters asked for in that window. Make sure you tick the format box and on mount point use the drop down box to select / as mount point.

---

### Post by buccaneere on 2009-12-28
Thanks!

Which parameter do I want - ext4?, ext3, ext2, or other?

I hope to have EVERYTHING, EXACTLY as it is now, except the new install...

---

### Post by presence1960 on 2009-12-28
> **buccaneere said:**
> Thanks!

Which parameter do I want - ext4?, ext3, ext2, or other?

I hope to have EVERYTHING, EXACTLY as it is now, except the new install...

ext4 is fast, but ext3 is ok also. Everything will be as it is now as long as you only change the Ubuntu partition on the manual option. leave every other partition alone. If you already have a swap partition leave that too as the installer will detect that and set it up to be used.

---

### Post by buccaneere on 2009-12-28
> **presence1960 said:**
> ext4 is fast, but ext3 is ok also. Everything will be as it is now as long as you only change the Ubuntu partition on the manual option. leave every other partition alone. If you already have a swap partition leave that too as the installer will detect that and set it up to be used.

Thanks again there!

And *THIS* partition is my mount point? It does not say that this is NOW the case, in my current setup... ?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141432&d=1261977634[/IMG]

---

### Post by presence1960 on 2009-12-28
Click use as and choose ext3 or ext4. Tick the format box. Then on mountpoint use the drop down box to choose /

Then click OK. The partitioner will rescan your disks and then you will see the info there.

---

### Post by buccaneere on 2009-12-28
> **presence1960 said:**
> Click use as and choose ext3 or ext4. Tick the format box. Then on mountpoint use the drop down box to choose /

Then click OK. The partitioner will rescan your disks and then you will see the info there.

Thanks again there presence!

Now, I'm finding 'No accounts found' (to import personal stuff).

It's all backed up - the 8.04 stuff, but if I can directly import it in the install, that would be better. How come it's finding no users/data?

---

### Post by presence1960 on 2009-12-28
> **buccaneere said:**
> Thanks again there presence!

Now, I'm finding 'No accounts found' (to import personal stuff).

It's all backed up - the 8.04 stuff, but if I can directly import it in the install, that would be better. How come it's finding no users/data?

That one I have to say I do not know. Since you got it all backed up you should be ok if it does not find anything to import.

---

