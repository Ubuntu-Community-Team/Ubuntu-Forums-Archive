---
title: "Evolution Contacts error message using Google"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2011-10-28
I have upgraded to 11.10 and am having error messages with the Contacts AddressBooks when using Google as an account.  I set up the account by gouing in to Add Addressbook, then selecting the Google option and then username and password.  It fails with all accounts, but ONLY in Contacts.

[HTML]Unable to open address book

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Cannot authenticate user: Invalid query[/HTML]The message is enclosed in a screen shot

Any ideas, please?

ANY HELP ANYONE, PLEASE???????

---

### Post by ElToro on 2011-11-07
I have got a similar problem after updating to 11.10. Evolution just fails to get my Goggle Contacts. The only difference from Jonners59's problem is that I do not get any error message at all. :confused: 

Tried to delete and add the address book again, but that didn't help. 

A solution would be greatly appreciated...

---

### Post by Jonners59 on 2011-11-07
Pleased I am not the only one.  Disappointed that no one has responded in support.  Hopefully an administrator will pop-in and nudge this one.

---

### Post by ElToro on 2011-11-09
Yes! Solved it! :popcorn:
Hopefully it works for everybody.

Do the following:

1) Close Evolution

2) Open up terminal and type:

```
evolution --force-shutdown
```3) Upon the successful termination of the Evolution process, type (still in terminal):

```
seahorse
```This opens up the password manager.

4) Under the password-tab, click on the Passwords: login - folder.

5) Right click on any password(s) related to Gmail in Evolution and select delete. Comfirm deletion in the pop-up window.

6) Restart Evolution and go to Contacts.

7) Re-enter your Gmail-account password.

This should get all your Gmail contacts up and going in Evolution. :guitar:

---

### Post by Jonners59 on 2011-11-10
No, not for me.  My tabs were empty, all of them.  I do not have any security keys.

Any more ideas, guys?????????

---

### Post by ElToro on 2011-11-10
Er... I think that's your problem right there; If you don't have any security keys you cannot connect to Google Contacts, right? Don't know what causes it, though... Or how to fix it...

---

### Post by donpeter06 on 2011-11-10
What all authentication methods have you choosen for your Gmail  other than password!!!
If you have please post it.

---

### Post by Jonners59 on 2011-11-10
None....

I have logged in to another machine that does work and tried this out and yes, in the tab there are lists of URLs and passwords...

How do I fix this???????????

PS Interestingly, the machine that does have these entries, I have problems with my Opera browser in that it does not remember the Usernames and Passwords!!!!!

---

### Post by Jonners59 on 2011-11-11
Sorted by reinstalling upgrade....  Seems to work again.  Thanks guys.

---

### Post by cantillon on 2012-09-03
ElToro's solution worked like a charm for me. Thanks a lot!

---

