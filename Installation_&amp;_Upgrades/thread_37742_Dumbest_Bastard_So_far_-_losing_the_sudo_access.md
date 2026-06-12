---
title: "Dumbest Bastard So far - losing the sudo access"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by Krank on 2005-05-28
OK, this might be the stupidest thing I've ever done, on any system, ever. In retrospect, a plethora of "shouldn't have" and "should have"'s manifest, but all that's left now is damage control.

I had just gotten my server just the way I wanted it. Ubuntu, Apache, the works.

I was playing around with user and group permissions, and managed to remove myself from the list of valid SUDO:ers. I had not yet defined a root password, so I cannot log on as root. I need sudo or su access in order to fix this - see my problem?

Anyways, I believe the problem is that I managed to place myself in the wrong group - from the group "krank" (default, my user name) to the group "remoteusers". The group "remoteusers" do not have sudo access. Is this a workable hypothesis?

If so, how can it be fixed? Can it be fixed? At all?

---

### Post by tread on 2005-05-28
You can boot into single mode. Edit the commandline arguments being passed to grub at boottime, and tag on "single" at the end.

---

### Post by Krank on 2005-05-28
First off, thank you so much for the quick reply. I can only bow my daft head in shame.

OK, so... Um... How do I find out what those commandline arguments are? And where, exactly, do I enter them?

I guess i'm supposed to press ESC (to get the GRUB menu), and select the first item, and press "e" to edit it... Should I just add a new line ("o") and edit it ("e") and write "single" and ENTER, and then press "b" to boot?

Or should the new line be elsewhere?

---

### Post by Krank on 2005-05-28
Nevermind, figured it out. Thank you so much!

---

