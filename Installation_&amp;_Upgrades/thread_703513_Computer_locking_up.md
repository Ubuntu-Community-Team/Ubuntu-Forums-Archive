---
title: "Computer locking up"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Newbie Ted on 2008-02-21
I just installed  Ubuntu 7.10 yesterday from a disk that came with the book "ubuntu 7.10 linux unleashed".  I have Pentium 4 and 768 RAM

Ubuntu  seemed to run OK yesterday with a few little things like getting evolution up and working. Today has been a different story 

Following instructions in the book, I  pressed 'ctl-alt-F1' to get to the command line prompt. All I got was a black screen with no prompt. My monitor went into sleep mode and the computer just locked up. It did respond to 'ctl-alt-delete' by restarting from boot but no other keys made a change.

Rebooted, I went to Terminal mode from Applications. That started up Ok and did respond to some commands. I then entered in '$ apt-get update' and I got a nice scroll. The book then tells me to do the upgrade by '$ apt-get dist-upgrade'. The computer again locks up responding to nothing. I had to pull the power cord. I restarted and in the upper right came a message that there was  one update. I clicked on the button, upgrade manager started and came to the screen showing what was to be updated. At this point again everything locked up and I needed to pull the plug. I did this twice and now in my frustration I am putting this posting up.

I thought this only was supposed to happen with MS stuff.

---

### Post by oilchangeguy on 2008-02-21
7.10 is the current version of ubuntu. 8.04 is still is beta. and therefore not available via the upgrade.

---

### Post by ronmarley1 on 2008-02-22
I'm sorry that you are having issues running the updates.  I'm not sure what the issue is.
The above poster is correct in that the current version is 7.10, so upgrading to 8.04, which is in Alpha (not Beta, by the way) stage of development, is not recommended for mission critical machines.
The poster is correct concerning the dist-upgrade command for upgrading.  But running ```
update-manager -d
``` from a terminal window will open the Update Manager and it will have a button to upgrade to 8.04.  But I'd wait to do that.

---

### Post by kool_kat_os on 2008-02-22
> **ronmarley1 said:**
> I'm sorry that you are having issues running the updates.  I'm not sure what the issue is.
The above poster is correct in that the current version is 7.10, so upgrading to 8.04, which is in Alpha (not Beta, by the way) stage of development, is not recommended for mission critical machines.
The poster is correct concerning the dist-upgrade command for upgrading.  But running ```
update-manager -d
``` from a terminal window will open the Update Manager and it will have a button to upgrade to 8.04.  But I'd wait to do that.

i just noticed that....thanks:)

---

