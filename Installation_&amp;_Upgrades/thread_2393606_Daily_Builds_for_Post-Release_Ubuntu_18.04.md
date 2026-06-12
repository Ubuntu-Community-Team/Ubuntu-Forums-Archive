---
title: "Daily Builds for Post-Release Ubuntu 18.04?"
date: 2018-06-05
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2018-06-05
I believe the daily builds are based on the yet-to-be-released 18.10.  As above-titled, I was wondering whether there are post-release daily builds for 18.04?

---

### Post by PaulW2U on 2018-06-05
Yes there are. These will in due course be released as Ubuntu 18.04.1 and for the subsequent point releases.

You can find them at [http://cdimage.ubuntu.com/bionic/daily-live/](http://cdimage.ubuntu.com/bionic/daily-live/)

---

### Post by #&amp;thj^% on 2018-06-05
Short answer nope.
You may start from a daily build, but that just means you're using whichever version's repository that daily build used. After the installation, all upgrades are a matter of the repositories used. Post-release, the daily builds are updated to use the next release's repositories.
So in short **sudo apt update **and **sudo apt upgrade** ends you in a so called post-release version.
I think Debian Rolling might do this but I just don't know for sure.
EDIT: Well i guess I stand corrected by PaulW2U, learn something new every day! :)

---

### Post by ping-wu on 2018-06-05
> **PaulW2U said:**
> Yes there are. These will in due course be released as Ubuntu 18.04.1 and for the subsequent point releases.

You can find them at [http://cdimage.ubuntu.com/bionic/daily-live/](http://cdimage.ubuntu.com/bionic/daily-live/)

Got it.  Thanks a whole bunch!

---

