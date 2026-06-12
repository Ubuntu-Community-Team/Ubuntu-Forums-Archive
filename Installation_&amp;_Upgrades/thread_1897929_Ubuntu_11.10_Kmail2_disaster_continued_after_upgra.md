---
title: "Ubuntu 11.10 Kmail2 disaster continued after upgrade to 4.7.3"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by swissinvestor on 2011-12-20
Today, after the automatic upgrade to Kmail 4.7.3 I have no ability to view or open emails anymore. 

It just stucks with the message "Retrieving Folder Contents...Please wait..."

Sending of emails did not work either, an akonatictl stop akonatictl restart did that.


My verdict on Kmail2 is now done: AVOID AT ALL COST, but too late for me unfortunately. 

Any ideas about alternatives would be appreciated too (with full PIM however, so TB is not a possibility)

Ubuntu 11.10 64-bit Kmail 4.7.3

---

### Post by cdunham on 2011-12-21
Agreed. All the years of filter rules, folders and saved emails make the prospect of switching a painful one, but at this point, kmail2 is such a pos, I am no longer able to functionally read email.

---

### Post by swissinvestor on 2011-12-24
Well, after 4 (Four!) days of having no access to emails, the "synchronizing..please wait.." screen suddenly vanished and I could read my emails again.

I have not the slightest idea why it suddenly works again.
My Inbox has 125 MB and altogether I have close to 10GB of data.
But 4 days to synchronize??

Whatever, it works again, but my strong feeling that I should get rid of Kmail as soon as possible has only gotten stronger and the tons of complaints I read about it are surely there for a reason as I learned as well.

---

### Post by swissinvestor on 2011-12-27
Never say something positive about Kmail2, it doesn't deserve it.

My problem is back, "retrieving folder contents..please wait" and no access to emails anymore since another day now. Again.

Kmail has become the most annoying garbage for me and part of the explanation of developers obviously giving a s... for users is probably explained in this blog:

[http://dilfridge.blogspot.com/2011/09/who-cares-about-users-and-distributions.html](http://dilfridge.blogspot.com/2011/09/who-cares-about-users-and-distributions.html)

yes, I am really getting annoyed

---

### Post by swissinvestor on 2011-12-28
[https://bugs.kde.org/show_bug.cgi?id=288364](https://bugs.kde.org/show_bug.cgi?id=288364)

There obviously is a bug introduced with the update to 4.7.3.

So we have lost email-access until the update to 4.7.4 is available?

(I read some people say the bug is gone with 4.7.4, others say the contrary).

What a mess Kmail has become.

---

### Post by RobTheBold on 2011-12-28
Sometimes the "Update Folder" function in the context menu gets the "Please Wait ... " to go away long enough to read a few messages. Sometimes not. Perhaps I just happened to have waited long enough.

The work-arounds I've read seem to suggest backing up all your messages, deleting the databases and configuration, reinstalling, restoring messages, re-creating accounts and all your filters, etc. If I were to go to that much trouble, I might was well be switching to another email client -- it would be the same amount of work.

I just don't need to be testing out a bleeding edge email client for my actual "production" work. I had no intention of that when a set up kmail in the first place. I suppose it's my own fault for not sticking with a LTS version of Ubuntu. I admit I didn't think kmail would get unstable, considering its importance to so many users.

Edit:

The "Update" thing was just a coincidence. Folder updating is still unusably slow.

---

