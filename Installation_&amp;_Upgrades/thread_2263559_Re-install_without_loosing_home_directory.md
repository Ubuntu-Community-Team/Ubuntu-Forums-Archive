---
title: "Re-install without loosing home directory"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by andyhelloween on 2015-02-01
Hello all,

I upgraded from 12.04 to 14.04, and after issues with video driver, I decided to perform a fresh re-install. I thought to get some reassurance on this process, as I have never done a re-install before and found post from other people who had trouble in the past.

As far as I understand it:

1) / is to be on the same partition as before, format checked.
2) /home is to be on the same partition as before, **format unchecked**.

Should I create the same user name I had before?
Wouldn't that overwrite the predefined directories like "Documents", "Music", "Videos", etc?
What about the various configurations saved on ~/.config and such?

...and before you said it, yes... backups are safe and sound.

Regards,
Andy.

---

### Post by Nutria on 2015-02-01
Where is your /home?  If on the same partition as /, then a fresh install would wipe out /home as part of formatting /. If /home is on it's own partition, then it's safe as long as -- as you mentioned -- you unckeck "format".

If /home is currently on the / partition, I strongly urge you to put it in it's own partition.  (/ only needs to be 30GB tops.  For example, mine only uses less than 10GB.)

> Should I create the same user name I had before?
Yes.

> Wouldn't that overwrite the predefined directories
No.

> What about the various configurations saved on ~/.config and such?
Ditto not overwriting predefined directories.

---

### Post by Bucky Ball on 2015-02-01
If on a separate partition, choose 'Something Else' when you get to the partitioning section of the Ubuntu install. As you mention, uncheck the formatting box, but set the partition to 'Use'. If you leave it as 'Do not use' then the install will create a /home directory in /. You can also set the existing /swap partition to not format but to 'Use'. No need for two /swap partitions. 

Double check that all other partitions are set to not format and 'Do not use'. 

Good luck, and good to see you have backups and are prepared for any mishaps. ;)

PS: Use a different username. Same password if you want. I have three installs, all using the same password but different usernames. Means I only have to remember one password, regardless of what I boot.

---

### Post by SeijiSensei on 2015-02-02
It doesn't really matter what username you choose.  The first user on a Ubuntu machine, the one created at installation, is assigned UID 1000.  If "bill" was UID 1000 before, but you use "william" this time, then all the files will be listed as owned by william.  Try listing a directory with "ls -ln" to see the numerical ownerships.  Usernames are just a convenience.

---

### Post by andyhelloween on 2015-02-05
Hello!

Thank you very much for the confirmation and explanations. I do have /home on a separated partition, so it was easy. As you said, no issues at all. I created the same user account of the original installation, and everything was there. Afterwards, I created the second user, and everything was there as well.

Once again, thanks much.
This is solved. ;)

---

### Post by Bucky Ball on 2015-02-05
Great news. Glad it all worked out, and thanks for marking as solved. ;)

---

