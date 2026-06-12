---
title: "after karmic upgrade"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 2roombas on 2009-10-25
Last night I upgraded my mini 9 with 9.10 karmic, and now when I boot up I'm greeted with...

    A hard disk may be failing.
    One or more hard disks report health problems.
    Click the icon to get more information

So I click the icon and get...

3.8 GB Hard Disk - ATA STEC ATA DISK vS020.1.0
DISK IS BEING USED OUTSIDE DESIGN PARAMETERS


Anyone else on a mini 9 get that? Does that mean I must stick with 9.04 on this mini now?

---

### Post by rockstarrem on 2009-10-25
Are you using the netbook edition? May be a stupid question, but just wondering.

---

### Post by Javi Pirate on 2009-10-25
Are you using clean install? or upgrade?

if you are using an upgrade i recommend you use a clean install

---

### Post by P4man on 2009-10-25
Its probably a bug. Many people are reporting similar issues, with excessive relocated sector counts. I wouldnt worry too much.
BTW is no way does this mean you would have to downgrade. Its a new feature that checks your drives' health but its a bit over enthousiastic at the moment, reporting when it shouldnt

---

### Post by rockstarrem on 2009-10-25
Good point whoever posted about the clean install. Especially with the new ext4 filesystem, this version should be clean installed.

---

### Post by P4man on 2009-10-25
A fresh install will give the same error as long as that new smart monitor misinterprets smart data. Dont have the bug link at hand, but its a known bug.

---

### Post by 2roombas on 2009-10-25
I did a clean install of both remix and regular, and they both had the error upon booting.   If I just hit esc then all seems to be fine, except I then will have that icon up in the panal taunting me.   Do you think this bug will be fixed, or will I always hace that error message whrn booting?

---

### Post by P4man on 2009-10-25
Who knows. Im still waiting for a few 3 year old confirmed bugs to be fixed.
But if not, you have the option "dont warn me if disk is failing" when you open the drive in palimpsest "disk utility"

---

### Post by Javi Pirate on 2009-10-25
> **2roombas said:**
> I did a clean install of both remix and regular, and they both had the error upon booting.   If I just hit esc then all seems to be fine, except I then will have that icon up in the panal taunting me.   Do you think this bug will be fixed, or will I always hace that error message whrn booting?


are you Karmic Koala release candidate?

---

### Post by 2roombas on 2009-10-25
> **Javi Pirate said:**
> are you Karmic Koala release candidate?

yes    I blame impatience!:P

---

### Post by Javi Pirate on 2009-10-25
> **2roombas said:**
> yes    I blame impatience!:P
 
The same error happen to me when I use karmic koala alpha ... xD

---

### Post by 2roombas on 2009-10-25
> **P4man said:**
> Who knows. Im still waiting for a few 3 year old confirmed bugs to be fixed.
But if not, you have the option "dont warn me if disk is failing" when you open the drive in palimpsest "disk utility"

Thank you!  I just did that... problem solved.:)

---

