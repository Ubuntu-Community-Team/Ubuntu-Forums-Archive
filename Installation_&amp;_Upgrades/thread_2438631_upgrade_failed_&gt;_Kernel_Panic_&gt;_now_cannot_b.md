---
title: "upgrade failed &gt; Kernel Panic &gt; now cannot boot to live USB version"
date: 2020-03-15
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2020-03-15
Hello.
I was running Ubuntu 16.xx (I can't remember what it was exactly and now that it's been blown away I can't check) and tried to upgrade to 18.04

At some point during the upgrade I glanced at the Terminal screen and saw a message along the lines of "Waiting for...... Ctl-C to continue (or maybe it said Quit).
Without thinking I hit whatever it said and seemed to kill the upgrade mid-process.

on rebooting I got the nefarious Kernal Panic - Not Syncing errors and a frozen screen.

"No problem" I thought. this was a rarely used system without any critical files on it. "I'll just reload 18.04 from a Live USB".
which I tried today but at each step of the Live CD (either "Run Ubuntu wtihout installing" or "Install Ubuntu...") I immediately sieze up on the Kernal Error - Not Syncing..... error.
I can get one step in (choose Language) but then it freezes up.

any suggestions as to what's going on or how to resolve this?

I thought booting a Live USB stick was pretty much foolproof.

---

### Post by yancek on 2020-03-15
Have you used the usb with Ubuntu 18.04 before successfully to boot it live?  If not, have you done and md5 or sha1 checksum on the iso to verify it was not corrupted in the process of downloading from the Ubuntu servers to your computer?
How did you put Ubuntu on the usb, what software did you use?

---

