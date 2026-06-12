---
title: "inet_wait_for_connect while trying to update from 9.04 to 9.10"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by LinuxGold on 2009-11-16
Tried to search for "inet_wait_for_connect" on forum to no avail, so I decided to post a thread for this problem.  Checked if it was already posted, but it wasn't.

I am running Ubuntu 9.04 server (kernel 2.6.28-16-server) on a Dell PowerEdge 1750 rack server with quad xeon processors entitled "motubuntu01".

Motubuntu01 is currently behind a proxy server and is configured correctly for package upgrades, and it is able to upgrade automatically.

Now I have been so busy with other projects and now am able to find a time to upgrade to 9.10 today.  I am using Update Manager and when I click on "Upgrade" button, it froze.  On system monitor "Waiting Channel" it said "inet_wait_for_connect".

I had to kill it, reran it and clicked on "check" it updated with various repo's and able to install a test package with no problem.

What is causing "inet_wait_for_connect" on Update Manager when everything else works?

---

### Post by LinuxGold on 2009-11-16
That's strange, when I posted this thread, and re-did the search on "inet_wait_for_connect" and found no thread with this string.  

Is there any thread that have solution to this problem "inet_wait_for_connect" that I am having and didn't show up on the search result?

Thanks,


Scott

---

### Post by Davie In Dubai on 2010-05-05
I've got exactly the same problem - did you find a fix?

---

