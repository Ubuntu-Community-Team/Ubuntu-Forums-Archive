---
title: "Gigabit ethernet throttled after upgrade 16.04.5 LTS to 18.04.1 LTS"
date: 2018-08-16
forum: Installation &amp; Upgrades
---

### Post by djchandler on 2018-08-16
Realtek RTL8111H gigabit lan now throttled to 100 Mb after upgrade in place from 16.04.5 to 18.04.1. Was running full speed before upgrade and have Google gigabit internet. Definitely 1/10 the speed. Checked at speedtest.net. Just completed today. Fixable or editable setting suggestions please.

[URL="https://www.gigabyte.com/us/Mini-PcBarebone/GB-BXi7-5775-rev-10#sp"]Full specs on my box here.
[/URL]
Thanks!

:confused:

---

### Post by djchandler on 2018-08-16
Figured this one out myself after walking away from it for a while. Still no sleep. Perhaps now.

Simple solution. Went to Setttings, Network and deleted the original 100 mb wired connection. There's a WiFi radio in the box too, so no real worries. Created a new wired connection, which was determined to be 1000 mb. Router was showing 1000 mb while still throttled to 100 mb on computer end. New 1 gb profile provided my solution.

Sounds like a minor bug.

---

### Post by QIII on 2018-08-16
Hello!

Let's not do the "me too" thing here, please.

Report the bug if you think that's what it is.

The "This bug affects me" clicks belong on launchpad.

---

### Post by djchandler on 2018-08-16
A single occurrence isn't necessarily a bug. Just saying that there's no use creating an issue on Launchpad if this was a one off. I solved my own problem at least. Here's the proof:

[https://ubuntuforums.org/attachment.php?attachmentid=280751&d=1534433495](https://ubuntuforums.org/attachment.php?attachmentid=280751&d=1534433495)
[https://ubuntuforums.org/attachment.php?attachmentid=280750&d=1534433468](https://ubuntuforums.org/attachment.php?attachmentid=280750&d=1534433468)
[COLOR=#000000]
[/COLOR]

---

### Post by QIII on 2018-08-16
All I am saying is that "me too" posts are not appropriate in a support area of the Forums.  We'll likely delete them.

---

### Post by djchandler on 2018-08-18
I edited my post above. The thread is marked "solved." Consider letting someone else benefit from my experience. Watch for view counts at least first.

Your posts are less than helpful.

There's now a new thread about you in the resolution center.

---

