---
title: "Root account password missing?"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by clh333 on 2005-07-08
Just completed the base install of ubuntu and in the process created a user account.  However, I seem to be without a password for the root account, and therefore cannot make changes to the system.  

Either I may have missed the opportunity to create one or there is a default of which I am unaware.  Anyone with suggestions on how to fix this?  Thanks.

-CH-

---

### Post by javiadip on 2005-07-08
Ubuntu doesn't use root account, by default its disabled. Instead of doing su, you do sudo -s -H or you can do like sudo <executions>, and for the password its the same as your user password.

---

### Post by crmanski on 2005-07-08
When it asks you for the root password to make changes try the one you set for your regular account.
mor info: [http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

---

### Post by RJARRRPCGP on 2005-07-08
[QUOTE=crmanski]When it asks you for the root password to make changes try the one you set for your regular account.
mor info: [http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)[/QUOTE]

I tried that, but it said that the password was wrong.

---

### Post by mingus on 2005-07-08
Dunno who this reply is going to . . . looks like this is another mixed thread.  In any case . . .

First, be sure you are set up in the sudoers file.  How to is at:
[http://www.ubuntuguide.org/#allowmoresudoers](http://www.ubuntuguide.org/#allowmoresudoers)

Then get in a terminal and do:
$sudo passwd root
enter your new root password & re-enter

Done.

---

### Post by woedend on 2005-07-08
click systems at the top, go to administration, then to users and groups.  Click that box that says show all users.  Select root, go to properties...set the pw.  now able to log in :).

---

