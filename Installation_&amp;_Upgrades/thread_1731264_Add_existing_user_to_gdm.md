---
title: "Add existing user to gdm"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by Fuji_in_Japan on 2011-04-16
Hello,

I recently switched to Ubuntu 10.10 x 64 from Mandriva.  I have four existing accounts from the Mandriva days and want to be able to use those accounts.

So problem one with the migration:

Only the new david account shows up in the gdm manager.  I wan to use the old dave as my primary account.  FYI I can log onto dave and am using KDE for that account.  That seems to be working fine.

How do I list the dave account in gdm so when I turn on the PC I have the choice of the two accounts?

Thanks,
Dave

---

### Post by zvacet on 2011-04-18
You can do that from system>administration>users & groups>edit account and add it to gdm.Second way is from CLI following [this]("https://help.ubuntu.com/community/AddUsersHowto") guide.

---

### Post by Fuji_in_Japan on 2011-04-18
zvacet,

Thank you for your reply.  I think I need to explain my problem more fully.  When I installed Ubuntu 10.10 I kept my old /home directory that was on a separate partition.  I had three user accounts already created and well used.  When I installed the new OS i created a david account.  the dave account UID 500 was my old Mandriva account.  I can log onto this account, but it does not appear on the gdm page.  I have to go to other, type in dave and then log on.

I would like for the dave account to appear as a choice I can click.

When I try to add the dave account, by the method you suggested I get that that account already exists.  So I am unable to get it into the gdm.

Dave

---

