---
title: "anyway to downgrade 8.04 to 7.10?"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Cephaus on 2008-05-14
Anyway to downgrade it without using the CD?

---

### Post by tamoneya on 2008-05-14
there is no downgrade path to 7.10 so you must do a fresh reinstall.

---

### Post by Cephaus on 2008-05-14
Damn, thanks anyway

---

### Post by tamoneya on 2008-05-14
i would recommend that you setup a seperate /home partition.  It will make any future installs much easier.

---

### Post by tighem on 2008-05-14
Linux is just about the easiest system to change systems on. Copy your /home directory over, reinstall, and then copy it back.

You'll have to reinstall any software, of course, but all your settings should be there...

---

### Post by trauma1914 on 2008-05-24
> **tighem said:**
> Linux is just about the easiest system to change systems on. Copy your /home directory over, reinstall, and then copy it back.

You'll have to reinstall any software, of course, but all your settings should be there...


Could someone tell me how to do this I really need to have all my settings reset I don't care about any software...

---

### Post by mikewhatever on 2008-05-24
> **trauma1914 said:**
> Could someone tell me how to do this I really need to have all my settings reset I don't care about any software...

Sure, check out this -> [https://help.ubuntu.com/community/?action=fullsearch&context=180&value=backup&titlesearch=Titel](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=backup&titlesearch=Titel)
I think using tar backup would be the easiest, since it does not need gui and can also be done from live cd.
> tar -cvpzf /destination/backup_home.tgz /home/your_user_name

---

