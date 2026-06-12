---
title: "Added an account, now can't remove it"
date: 2009-11-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-07
Using Lucid 2.6.32-2 kernel, I thought I'd take a look at adding a new user via Users and Groups when using my default account. Tried logging out and back in with both my default user and the new user. I then decided to remove the new account via Users and Groups (after logging this user out) and the account was no longer displayed. Closed Users Settings Window. I then tried to delete the new users Home folder via Nautilus and get the message 'The folder ".update-notifier" cannot be handled because you do not have permissions to read it.' How do I remove this (I haven't set up a superuser password) ?
If I re-open Users and groups the new user is still displayed.
Also it seems that I now have some files in my Wastebasket, but the basket when opened is empty. I can't remember where the files reside (via Nautilus) in order to delete them.
Is this a bug or user error ?

---

### Post by LKjell on 2009-11-07
sudo deluser --force --remove-home <username>

Try that first

---

### Post by MacUntu on 2009-11-07
Confirming the problem with deleting users using users-admin, using deluser works fine.

---

### Post by Kevbert on 2009-11-08
Thanks for that, worked a treat. The three files reported as being in the wastebasket (but not visible and not hidden) were removed on rebooting the PC.

---

