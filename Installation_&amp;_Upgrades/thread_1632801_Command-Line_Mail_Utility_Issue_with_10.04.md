---
title: "Command-Line Mail Utility Issue with 10.04"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by bsntech on 2010-11-28
Just upgraded from 8.04 to 10.04 on one of my servers.

I have a few logs that are sent to my e-mail address daily via cron jobs.

Well, one was trying to send out but it wouldn't work after upgrading to 10.04.

When the mail command-line is called and I put in the typical variables like I always did:

mail <mail-account> -s "Subject"

It just hangs and does nothing.

Further searching, I found to hit Ctrl+D and it would ask for Cc: information.

This is bad - now the mail utility cannot be used like it was for years where you just enter one command and it is done.  This won't work for cron jobs.

Has anyone managed to find a solution for this issue?

Thank you!

---

### Post by bsntech on 2010-11-28
This must be a hard one to figure out.

What I don't understand is this - whenever one of the cron jobs has an error or a exit code of 1 (meaning it didn't complete properly), I get an e-mail with the error information.  So, there must be some easy way to send mail out since the system can do it..?

---

