---
title: "Cups will not start on new installation of Natty"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by thetechnaddict on 2011-05-17
I am unable to print on a new installation of Natty.

The print configuration utility reports that no printing service is available.

I have comfirmed that cups is installed and get a positive response to "whereis cupsd"

When I attempt to start cups from the cl (service cups start) I receive the following response:


start: Rejected send message, 1 matched rules; type="method_call", sender=":1.63" (uid=1000 pid=5577 comm="start cups ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

There are no errors produced in the logs - either cups or syslog and if I turn apparmour to complain mode nothing improves:

sudo aa-complain cupsd

I am aware of this post:

[http://islandlinux.org/es/howto/upgrading-ubuntu-breaks-printer-cupsys](http://islandlinux.org/es/howto/upgrading-ubuntu-breaks-printer-cupsys)

but since the workaround has no effect and in the absence of error messages I am not sure that it applies and cannot implement - 

and note that no print drivers are in play since I can't get cups to start...

Can anyone give me any pointers please?

What should I try next?

---

### Post by Billxyzzy on 2011-05-17
I, also ,have been having printer problems.
See these launchpad bugs 769241 783974. I filed the
second one when I saw your post and realized it was the
same basic problem.  Please add your me-to to the bug
reports.  If you can add any additional info it would help.
We have to use a bigger 2 x 4 to to get some attention.

---

### Post by thetechnaddict on 2011-05-18
cups has come up - no idea why or how, but it is working.

I have switched to classic (gnome) desktop and back again... but then I've also had something to eat and been to sleep which may have as much relevance..

I'm pleased to be able to print, but sorry that my fortune will not help anyone...

---

