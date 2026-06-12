---
title: "SkyPE  - Contacts Status Not Showing."
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tom_T on 2009-04-16
Anyone have SkyPE working on Jaunty ??

Since upgrading Ubuntu only a couple of my contacts status changes.

Most are shown as offline, but I know a couple are online (my wife is on her skype account talking) but she and the other party are not showing as online..

Any ideas ?? I'm using the skype deb package from their website.

Thanks :)

---

### Post by bw44 on 2009-04-17
> **Tom_T said:**
> Anyone have SkyPE working on Jaunty ??

Since upgrading Ubuntu only a couple of my contacts status changes.

Most are shown as offline, but I know a couple are online (my wife is on her skype account talking) but she and the other party are not showing as online..

Any ideas ?? I'm using the skype deb package from their website.

Thanks :)

It may be a different problem altogether (and I'm still running with Hardy Heron), but yesterday I assisted another user in setting up their Skype account, and recieved the Skype email message asking if I wanted to accept them as a contact.  But when I search on their Skype name or email address they aren't found.  I booted up Windows and its version of Skype could find and add them to my contact list.  Then I went back to Ubuntu and Skype shows they have been added to my contact list but it still can't find them when I do a search.

I'm running the 2.0.0.72Medibuntu version of Skype installed with Package manager.

This probably doesn't help except to suggest that there might in fact be a Linux/Skype problem, rather than a Jaunty problem.

---

### Post by Tom_T on 2009-04-18
Thanks..

I'll post on the skype forums and see if they have any ideas !!

---

### Post by bw44 on 2009-04-18
> **Tom_T said:**
> Thanks..

I'll post on the skype forums and see if they have any ideas !!

I'm not sure where all the Skype forums are, but I visited the developer site and looked through all the issues with contacts for the Linux version.  Only one sounded remotely related to the problem I described in my previous post, so I reported it as a bug.  You can see what I posted at: [https://developer.skype.com/jira/browse/SCL-476](https://developer.skype.com/jira/browse/SCL-476)

You might want to have a read through the other problems reported at the above site; one of them sounds something  like what you described in your first post:> Most are shown as offline, but I know a couple are online (my wife is on her skype account talking) but she and the other party are not showing as online..

Cheers and good luck!

bw44
PS. Here's the URL for the list of problems with Linux Skype contacts: [https://developer.skype.com/jira/secure/IssueNavigator.jspa?reset=true&mode=hide&pid=10033&sorter/order=DESC&sorter/field=priority&resolution=-1&component=10082](https://developer.skype.com/jira/secure/IssueNavigator.jspa?reset=true&mode=hide&pid=10033&sorter/order=DESC&sorter/field=priority&resolution=-1&component=10082)

---

### Post by bw44 on 2009-04-18
Just to let anyone know who picks up on this thread:

When the new contact came online with Skype I was able to search for and find them with the Linux client. 

There still seems to be a difference in the ability of the Windows and Linux clients to search for new users as described in the following exchange on the Skyp community forum:  
[http://forum.skype.com/index.php?showtopic=249911](http://forum.skype.com/index.php?showtopic=249911)

The problem has been reported as a bug on the Skype DevZone jira site as:
[https://developer.skype.com/jira/browse/SCL-441](https://developer.skype.com/jira/browse/SCL-441)

Hope this helps.

bw44

---

