---
title: "Issue with Thunderbird"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by euphgeek on 2011-10-16
So with a bit of difficulty, I upgraded to 11.10.  I noticed that Evolution wasn't working the way it should and my e-mails were no longer showing.  After a little research, I found my e-mails and migrated them over to Thunderbird as I had been dissatisfied with Evolution for a while now anyway.

The only problem I've encountered with Thunderbird so far, is that every so often it will pop up a window with the following text in it:

```
There was a problem opening the address book "Bigfoot" - the message returned was: Cannot open book: Repository offline
```

I've searched the internet for that error message and have found nothing.  I've tried deleting the Bigfoot folder from my address book but it keeps giving me a message that it can't be deleted and coming back whenever I restart Thunderbird.  This doesn't happen at all with the same version of Thunderbird on Windows.  Anyone have any ideas here?

---

### Post by euphgeek on 2011-10-16
The message it gives me when trying to delete the address book Bigfoot is:

```
Sorry - this version of EDS Contacts Integration does not support deleting Evolution address
books. Due to the way that Thunderbird tries to delete address books, all of your EDS address
books will appear to be removed from the address book manager. Simply restart Thunderbird
in order to have them return.
```

---

### Post by euphgeek on 2011-10-16
So far, I have tried the following with no luck:

1. Deleted the Bigfoot address book from Evolution (it refuses)
2. Uninstalled evolution, evolution-couchdb, evolution-exchange, evolution-plugins, libevolution and evolution-data-server
3. Deleted all files from ~/.cache/evolution/addressbook, including a folder named "ldap___ldap.bigfoot.com_389_??one"

---

### Post by euphgeek on 2011-10-17
Turns out the solution was a simple one.  All I had to do was disable the EDS Contact Integration add-on in Thunderbird.

---

