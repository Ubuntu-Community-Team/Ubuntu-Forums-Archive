---
title: "How long before I can expect to upgrade from 16.04 to 18.04?"
date: 2018-08-05
forum: Installation &amp; Upgrades
---

### Post by operator-error on 2018-08-05
Like the subject says, how long before I can expect to be able to upgrade from 16.04LTS to 18.04LTS?  I've been patiently waiting for something to pop-up in my Updater, along with doing "sudo do-release-upgrade" in my terminal, but nothing so far, despite that the 18.04.1 upgrade has been available for several days now.  Here's a current snapshot of my system:

[http://paste.ubuntu.com/p/JdJp8TTX6T/](http://paste.ubuntu.com/p/JdJp8TTX6T/)

Any advice would be appreciated.

---

### Post by westie457 on 2018-08-05
Open 'Software & Updates', find the section 'download from' and change to 'main server' and check that you are set to be informed of latest LTS release. Reload the repos then check for updates. Possibly you now have chance to upgrade.

---

### Post by kansasnoob on 2018-08-05
I posted about this recently:

[https://ubuntuforums.org/showthread.php?t=2397260&p=13789257#post13789257](https://ubuntuforums.org/showthread.php?t=2397260&p=13789257#post13789257)

---

### Post by westie457 on 2018-08-05
Hi kansasnoob, have read that post.
In the first post here the op is using a mirror that may or may not be behind the main server. Which is possibly another reason they have not been given a chance to upgrade.
On a side note I have a machine running 14.04 with latest point release, that is set 'to not check for new release'.
When the time comes it will have a clean install of whatever release is available.

---

### Post by freesitebuilder on 2018-08-06
This worked for me - I also had to change upgrade option to "all releases" from "LTS releases".

---

### Post by operator-error on 2018-08-08
Okay, thanks all for your replies.  I'll give it a shot.

---

### Post by kansasnoob on 2018-08-09
There actually is a reason:

[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html)

I hope those choosing to change release notifications to "any new release" remember to change it back to LTS only after the upgrade so they don't end up on 18.10 unintentionally in a couple of months :eek:

---

### Post by operator-error on 2018-08-10
Update:
Changing my mirror to "Main Server" or "US Server" hadn't done anything.
However, changing my option from "LTS Releases Only" to "Normal Release" did.  So, I upgraded.  The only hiccup I experienced afterward (aside from my having to reassign my panel icons) was DNS seemed to be on the fritz.  Network connectivity was still there (IP addresses only), but name resolution wasn't working.  It seemed to fix itself, oddly, because name resolution came back after a couple restarts.  I'm not sure what happened there but, whatever.
And yes, kansasnoob, I changed my option back to "LTS Releases Only" after I upgraded (thanks) :)

---

### Post by fyfe54 on 2018-08-10
Thanks for the reminder about changing back to LTS only.  I did that once....

---

