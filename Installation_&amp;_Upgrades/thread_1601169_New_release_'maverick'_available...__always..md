---
title: "New release 'maverick' available...  always."
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by tranzmatt on 2010-10-19
I recently upgrades to Maverick on my x86_64 box.  All went fine, except now whenever I ssh into it, the /etc/motd always spits out:

[INDENT]Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

996 packages can be updated.
0 updates are security updates.

New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Tue Oct 19 21:51:01 2010 from bob
[/INDENT]

I don't like anything in my /etc/motd, so I deleted the contents, but it's always repopulated.  I googled around and tried purging and reinstalling update-manager, update-manager-core and update-notifier, but it still keeps popping up.  Can anyone help me figure this out?

---

### Post by Slim Odds on 2010-10-19
Well... according to that screen, you're running Lucid.

Did the upgrade go cleanly?

---

### Post by efflandt on 2010-10-20
What do you get for: **cat /etc/*release**

If the upgrade completed successfully you should get:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Kernel version may also give a clue.  What is the output of: **uname -a**

---

### Post by Bee77 on 2010-10-22
I have this issue too on different 10.10 machines.

/etc/lsb-release shows I'm using Maverick and the update from Lucid to Maverick ran just fine.

I think the problem is the /etc/motd.tail file. All text about 10.04.1 LTS is still visible in /etc/motd.tail, last update on the same day I updated to Maverick.

I've removed /etc/motd.tail and now the old messages don't appear any longer. When I ssh to a machine it says "Ubuntu 10.10" etc. but no "10.04*".

Can you test this in your environment?

Regards

---

### Post by mörgæs on 2010-10-22
Correct, that is the solution.
[http://ubuntuforums.org/showthread.php?t=1593161](http://ubuntuforums.org/showthread.php?t=1593161)

---

### Post by Bee77 on 2010-10-23
> **mörgæs said:**
> Correct, that is the solution.
[http://ubuntuforums.org/showthread.php?t=1593161](http://ubuntuforums.org/showthread.php?t=1593161)

Thanks for the link, mörgæs. That thread also contains a link to a bug report on launchpad ([https://bugs.launchpad.net/ubuntu/+bug/660470](https://bugs.launchpad.net/ubuntu/+bug/660470)).

---

### Post by Zeromaru on 2010-10-27
I've been having the same issue, however the fix didn't work for me the way it should. It removed the double message, but still displays old information from before updating to Maverick.

A secondary issue, which might be related, the default folder of any new shell is / instead of ~. I've checked all the appropriate environmental variables and user settings, nothing is set wrong.

EDIT: A restart actually did correct the message. The default folder issue remains, but I shall start a new topic for that.

---

