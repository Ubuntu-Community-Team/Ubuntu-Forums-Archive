---
title: "upgrade from 8.04 to 9.10"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by techbrainless on 2009-12-04
Hi All,
I am newbie , currently am working on ubuntu 8.04 i have downloaded the cd of 9.10 desktop and i want now to upgrade , so any one can tell me the steps to do that or i have to format my machine and install 9.10 .

---

### Post by phillw on 2009-12-04
> **techbrainless said:**
> Hi All,
I am newbie , currently am working on ubuntu 8.04 i have downloaded the cd of 9.10 desktop and i want now to upgrade , so any one can tell me the steps to do that or i have to format my machine and install 9.10 .

Hi,
You can upgrade 8.04 --> 8.10 --> 9.04 --> 9.10 ... Which seems a lot of work !!

Or, you can backup your user data & do a clean install. In your case, I think a backup & fresh install with 9.10 would be the better option, as it will give you ext4 natively & also Grub2.

Regards,

Phill.

---

### Post by ajgreeny on 2009-12-04
I do not think you can do that in one jump as an update.  If it were me, I would backup all personal files and the few important hidden .config folders from home and start again with a new clean install.

If you wait a few months for 10.4, which is another LTS version, you can in theory do an online upgrade to the new version.  I have never upgraded online at all, however, so I am really the wrong person to tell you what is the best course of action, though generally I get the impression that clean installs present less problems to users.

---

### Post by phillw on 2009-12-04
> **ajgreeny said:**
> I do not think you can do that in one jump as an update.  If it were me, I would backup all personal files and the few important hidden .config folders from home and start again with a new clean install.

If you wait a few months for 10.4, which is another LTS version, you can in theory do an online upgrade to the new version.  I have never upgraded online at all, however, so I am really the wrong person to tell you what is the best course of action, though generally I get the impression that clean installs present less problems to users.

+1 on a clean install. As 10.04 will be heavily based on 9.10 - it does give you chance to get used to it & iron out any machine specific 'gotchas' with audio / video etc !!

The LTS will be using Grub2 and ext4 - so 9.10 is a great prelude to it.

REgards,

Phill.

---

