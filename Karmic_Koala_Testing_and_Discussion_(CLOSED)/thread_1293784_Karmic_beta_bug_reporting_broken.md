---
title: "Karmic beta bug reporting broken"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by K7AAY on 2009-10-17
At the link for bugs in the Karmic beta
[https://bugs.launchpad.net/ubuntu/+s...oftware-center](https://bugs.launchpad.net/ubuntu/+s...oftware-center)
I click on the link titled
Report a Bug
which should take me to
[https://bugs.launchpad.net/ubuntu/+s...enter/+filebug](https://bugs.launchpad.net/ubuntu/+s...enter/+filebug)
but instead, I go to
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
and get the message (even after I completely clear my browser cache) 

--

ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: 
[http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs)

The following error was encountered:

* Unable to forward this request at this time.

This request could not be forwarded to the origin server or to any parent caches. The most likely cause for this error is that:

* The cache administrator does not allow this cache to make direct connections to origin servers, and
* All configured parent caches are currently unreachable.

Your cache administrator is webmaster.

--

#2) 'webmaster' is a broken mail link and cannot be contacted.

---

### Post by todak on 2009-10-17
Look [here]("http://manpages.ubuntu.com/manpages/karmic/man1/ubuntu-bug.1.html") and see if this will help you. :)

---

### Post by K7AAY on 2009-10-17
> **todak said:**
> Look [here]("http://manpages.ubuntu.com/manpages/karmic/man1/ubuntu-bug.1.html") and see if this will help you. :)

Does not help. My sole Linux box is broken, and what you provided is Linux-specific. Need to report using my other machine which is not Linux.

Also does not address problem 2)

---

### Post by philinux on 2009-10-17
Whats wrong with the info here.

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

Link is provided.
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

This an attempt to get better reported bugs either with apport or ubuntu-bug. However the no-redirect link is what you're after.

---

