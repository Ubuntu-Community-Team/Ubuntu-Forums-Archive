---
title: "Error Message after 13.04 upgrade - W/ Address Book &amp; Credentials"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by acimi66 on 2013-05-02
This only happens once after booting up.

I click on thunderbird to check mail. And I get this warning message.

[B]
"There was a problem opening the address book "Contacts" - the message returned was: 
Cannot open book: GDBus.Error: org.gnome.OnlineAccounts.Error.NotAuthorized: 
Did not find password with username `c..............s@gmail.com' in credentials."[/B]

I can close thunderbird and open it again later, no message.

This account c.............s@gmail.com is a part of my online accounts.

Any Ideas?

---

### Post by francoiselabelle on 2013-05-02
Hi, 
it's filed as a bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-online-accounts/+bug/1152490](https://bugs.launchpad.net/ubuntu/+source/gnome-online-accounts/+bug/1152490)

The solution down the page worked for me: I disabled EDS contact integration add-on.

Francoise

---

### Post by acimi66 on 2013-05-03
Thanks for the link Francoise but I don't really want to loose intergration with my online accounts.

I'll keep looking.
Cheers

---

### Post by acimi66 on 2013-07-13
I finally had to go with: uninstall **gnome-online-accounts**. I did this through the SC.

---

