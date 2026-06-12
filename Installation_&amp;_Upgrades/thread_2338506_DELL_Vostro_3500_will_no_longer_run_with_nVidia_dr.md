---
title: "DELL Vostro 3500 will no longer run with nVidia drivers"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2016-09-28
I had to leave Ubuntu 16.04 this afternoon and boot into Win XP Pro SP3 to use a non-linux application.  This is something I have done hundreds of times without problems.  We I rebooted back into 16.04, the logon screen was noticeably distorted, like something was wrong with the video driver.  Each login attempt resulted in the logon screen coming back.

Got a CLI, and purged nvidia* and then rebooted.  Everything back to normal, but with nouveau video driver.  Attempts to reinstall nvidia driver 304-132 from synaptic brought back the wrong logon screen.

What is going on?

Thank you,

John

---

