---
title: "Email error when sending after Ubuntu upgrade"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by Kanichiro on 2013-01-15
I am using Evolution for my email client. After upgrading Ubuntu, I now receive an error message when I send an email. 

Also, I discovered that my Contact list was not visible and I needed to "un-check" the Personal option from the preferences under Contacts in order to be able to see my contacts. However, when I click Contacts from the list in Evolution all my contacts are listed under "On This Computer > Personal."

Attached is a screen shot of the error I am receiving. 

The two blacked out sections in the path contain my real user name.

I'm running a duel-boot system. Ubuntu 12.10/Windows 7. Attached is a screen shot showing my system info on the Ubuntu side.

Thanks for any/all help anyone might provide!

I am not sure how to fix this.  It's kind of a pain as I need to close the error message each time I send an email.


Edit: I found the cause of this issue. On the Account Editor > Defaults tab, there are two drop-down lists for Special Folders. 1) Draft Message Folder, 2) Sent Message Folder.

When I upgraded these settings got deleted. I had to reset these folders to my Draft and Sent folders.  This ended the error I was receiving.

---

