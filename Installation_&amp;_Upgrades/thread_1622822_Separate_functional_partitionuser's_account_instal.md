---
title: "Separate functional partition/user's account installation"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-15
How can I implement this: 
I encrypt a partition using LUKS, and store personal data on this  partition. Then create a user account that solely deals with this  partition and insulated from the Internet. Normally for each boot I do  not even need to mount the LUKS encrypted partition, and when I mount  that partition under that special user account, I can make sure that the  Internet is cut off.

I'm going to do the alternate installation these days, could you provide  a brief sketch regarding what steps I should go through to implement  the above result? Thank you.

---

### Post by shadowofblood on 2010-11-15
So basically...

You want to be able to access the encrypted partition from ONLY one user account that has no internet access?
Or do you want the internet access to simply cut off when the partition is mounted?
Do you want to be able to access the partition from other user accounts at all?

---

### Post by zhaotianwu on 2010-11-16
> **shadowofblood said:**
> So basically...

You want to be able to access the encrypted partition from ONLY one user account that has no internet access?
Or do you want the internet access to simply cut off when the partition is mounted?
Do you want to be able to access the partition from other user accounts at all?

Hi shadowofblood,
You are right, I want "to be able to access the encrypted partition from ONLY one user account that has no internet access". And I do NOT need to be able to access the encrypted partition from other user accounts. And I want this encrypt this partition using LUKS full-partition encryption. Any ideas on how to implement this? Thanks.

---

