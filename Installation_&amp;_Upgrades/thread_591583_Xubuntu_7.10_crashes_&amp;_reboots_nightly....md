---
title: "Xubuntu 7.10 crashes &amp; reboots nightly..."
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Sporkman on 2007-10-25
Xubuntu 7.04 was fine, then I upgraded to 7.10. Sometime since then (not sure exactly when or why), I've been regularly waking up to a rebooted machine. Here's what the syslog says since the last one:

Oct 24 07:10:45 neamakri -- MARK --
Oct 24 07:17:02 neamakri /USR/SBIN/CRON[6136]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 24 07:30:01 neamakri /USR/SBIN/CRON[6140]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Oct 24 07:30:02 neamakri anacron[6165]: Anacron 2.3 started on 2007-10-24
Oct 24 07:30:02 neamakri anacron[6165]: Will run job `cron.daily' in 5 min.
Oct 24 07:30:02 neamakri anacron[6165]: Jobs will be executed sequentially
Oct 24 07:35:03 neamakri anacron[6165]: Job `cron.daily' started
Oct 24 07:35:03 neamakri anacron[6172]: Updated timestamp for job `cron.daily' to 2007-10-24
Oct 24 07:35:16 neamakri gdm[4722]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

I'm not sure if it's a 7.10 issue alone, or if I've done something or had something open that disagrees with 7.10. Has anybody else seen this?

BTW It's on a Gateway Solo 9300 laptop.

---

