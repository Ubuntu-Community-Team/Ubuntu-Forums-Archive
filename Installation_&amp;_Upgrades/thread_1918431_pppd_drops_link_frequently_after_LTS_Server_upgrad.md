---
title: "pppd drops link frequently after LTS Server upgrade from 8.04 Hardy to Lucid 10.04"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by FrankAu on 2012-01-31
I have just upgraded an LTS Server system from 8.04 Hardy to 10.04 Lucid and now pppd is dropping the serial link at frequent intervals after complaining that it has not seen any echo-requests.
/var/log/messages ...
Feb  1 09:59:22 gmmp pppd[23446]: No response to 3 echo-requests
Feb  1 09:59:22 gmmp pppd[23446]: Serial link appears to be disconnected.
Feb  1 09:59:22 gmmp pppd[23446]: Connect time 746.3 minutes.
Feb  1 09:59:22 gmmp pppd[23446]: Sent 1023444758 bytes, received 46425646 bytes.
Feb  1 09:59:23 gmmp pppd[23446]: Connection terminated.
Feb  1 09:59:23 gmmp pppd[23446]: Terminating on signal 15
Feb  1 09:59:23 gmmp pppd[23446]: Exit.
...
Feb  1 10:31:59 gmmp pppd[26545]: pppd 2.4.5 started by root, uid 0
Feb  1 10:31:59 gmmp pppd[26545]: Serial connection established.
Feb  1 10:31:59 gmmp pppd[26545]: Using interface ppp0
Feb  1 10:31:59 gmmp pppd[26545]: Connect: ppp0 <--> /dev/pts/0
Feb  1 10:32:01 gmmp pppd[26545]: PAP authentication succeeded
... and ...
# egrep -v '^#|^$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
+pap
debug
proxyarp
lcp-echo-interval 30
lcp-echo-failure 6
lcp-restart 5
pap-restart 9
pap-timeout 30
noipx
persist
maxfail 0
holdoff 5
#
... however the "persist" option does not seem to have any effect?!?
When the upgrade was progressing the choice to NOT upgrade configuration files with new distro information was selected - and the only break/fix required was for dovecot as I recall.  Is there a way to find what the Lucid version of the /etc files look like?
Cheers, Frank.

---

### Post by FrankAu on 2012-02-03
Hmmm - it is starting to look like the issue is being triggered by an rsync transfer of a database dump to a remote host.

Both systems are Lucid 10.04 LTS however the problem server is DSL connected with pppoe and the remote server is cable connected.  MRTG shows the link is maxed out for an hour or so.

Since I have disabled the backup process the link hasn't failed.

I will go back through the logs to see if I can find a correlation.

---

### Post by FrankAu on 2012-02-06
Issue is multi layered ... on my analysis to date it seems ...

1. after a long squawk from rsync - pppd feels compelled to have a rest (per the Norwegian Blue) likely due to the severely lagged echo-requests not being answered in a timely fashion.  There does not appear to be a bug logged on this topic so I assume this is not unexpected or deemed unreasonable ... but I beg to differ, and then ...

2. when this happens - udev kills pppd but thereafter there is no pathway to bring it back up again.  Several rants as far back as 2007 exist and Ubuntu bug #78043   - "udev stops pppd persist working" seems to explain why the restart fails to happen.

---

### Post by FrankAu on 2012-02-14
OK - tried to get a restart happening - no joy - more debugging to come.

One disturbing outcome of the test was that pppd died in the middle of the rsync session ... not (as I had expected) just after the rsync wrapped up and eased off the gas!  On the surface it seems it was so busy moving data it didn't get around to resolving the keep alive packets.

My initial reading of it is that Lucid pppd has been messed up - because with Hardy, for more than 12 months of heavy rsync every night, there was not one glitch.

---

### Post by FrankAu on 2012-02-20
Some progress ... using rsync --bwlimit (on a massive sample size of 1 use) seems to have left enough air for the echo requests to keep the link alive.  I still reckon pppd is bugged though!  Will have a scratch around the bug register for likely suspects.

---

### Post by FrankAu on 2012-02-20
Doh - wrote too soon!!!

Although the link was working at 07:10 and rsync was killed at 07:30 pppd still crapped out ... logs below ... curiously although rsync kept going until 08:22 whilst pppd crashed at 07:57?!?  Next to check bugs and more research on auto restart.

rsync.sh log
--------------
20120221 01:00:01 /data/rsink.sh rsync commenced
receiving incremental file list
...
20120221 07:30:01 pause initiated
Write failed: Broken pipe
rsync: writefd_unbuffered failed to write 4 bytes to socket [generator]: Broken pipe (32)
rsync: connection unexpectedly closed (817315397 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(1530) [generator=3.0.7]
20120221 08:22:08 /data/rsink.sh completed

/var/log/messages
----------------------
Feb 21 07:57:43 gmmp pppd[1051]: LCP terminated by peer
Feb 21 07:57:43 gmmp pppd[1051]: Connect time 12238.2 minutes.
Feb 21 07:57:43 gmmp pppd[1051]: Sent 1215102079 bytes, received 1108817406 bytes.
Feb 21 07:57:46 gmmp pppd[1051]: Modem hangup
Feb 21 07:57:46 gmmp pppd[1051]: Connection terminated.
Feb 21 07:57:46 gmmp pppd[1051]: Terminating on signal 15
Feb 21 07:57:46 gmmp pppd[1051]: Exit.

---

### Post by FrankAu on 2012-02-28
Latest update ...

I have changed the rsync command by adding "--bwlimit 150" expecting to leave** a little spare bandwidth for the echo-requests to be exchanged.

This seems to work as the mrtg charts show the traffic flat lining at 300 kbs and an uneventful completion last night.

** the soliciting system is on a cable link that has a much higher throughput than the providing system on a slower DSL link.

---

