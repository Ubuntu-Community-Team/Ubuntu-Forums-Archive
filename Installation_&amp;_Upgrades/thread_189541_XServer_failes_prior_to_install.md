---
title: "XServer failes prior to install"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by markr on 2006-06-05
Strange problem which I have seen before (I've been installing via the flights for a while now with no issues).

I downloaded the destop iso and burnt it onto CD,  stick it in the drive and reboot.

I get a nice graphical menu and select the first option (start or install).

After ubuntu runs for a while (trying to configure network and the like), I get a nice blue screen telling me the display server shut down 6 times and something bad is going on.

I have never had this problem before installing either breezy or the RC.  Any thoughts?

I'm assuming it must be something to do with configuring my Geforc 5200Go, but must admit I'm a bit puzzled

Mark.

---

### Post by markr on 2006-06-06
Bump???

Really need to get this resolved as I'm unable to install Dapper :-)

---

### Post by toLa` on 2006-06-06
did you check the media for errors? (MD5 checksum / option under LIVE boot cd)

---

### Post by tones111 on 2007-10-13
I'm having the same problem on the Gutsy release candidate (even when using safe graphical mode).  Everything comes up fine using Gutsy Tribe 4.  I've checked md5 values and the CD verification passes.  I've entered a bug report on launchpad (bug #152379).  Any idea on how to get more debugging information?

---

### Post by EtiennePhillips on 2007-11-09
I got around this by hitting ctrl+alt+F5, and logging in (if you're on the LiveCD, you don't need to log in).

run "ps -A | grep gdm"

"sudo kill [pid]" the pid's of the 2 processes listed by the above command.

run "startx"

This is also on my EX15000G. Beats me why it's happening. I was hoping it was just an install issue, but it appears to be happening on bootup too. PITA...

---

