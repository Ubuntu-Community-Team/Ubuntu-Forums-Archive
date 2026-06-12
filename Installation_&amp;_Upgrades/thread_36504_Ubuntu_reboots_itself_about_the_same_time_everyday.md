---
title: "Ubuntu reboots itself about the same time everyday."
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by sfuhrman on 2005-05-23
I am having a weird problem with my Ubuntu box.  Every morning between 7:35 and 7:40 the system is restarting itself.   Has anyone else seen this?  This is bizarre to me and I have not seen it on the same machine with other distros.


```
root@crappie:/dev # cat /var/log/messages.0 | egrep "signal|restart"

May 14 07:35:16 crappie exiting on signal 15
May 14 07:35:17 crappie syslogd 1.4.1#16ubuntu6: restart.

May 15 07:35:19 crappie exiting on signal 15
May 15 07:35:20 crappie syslogd 1.4.1#16ubuntu6: restart.

May 16 07:35:16 crappie exiting on signal 15
May 16 07:35:17 crappie syslogd 1.4.1#16ubuntu6: restart.

May 17 07:35:17 crappie exiting on signal 15
May 17 07:35:18 crappie syslogd 1.4.1#16ubuntu6: restart.

May 18 07:36:25 crappie exiting on signal 15
May 18 07:36:26 crappie syslogd 1.4.1#16ubuntu6: restart.

May 19 07:36:26 crappie exiting on signal 15
May 19 07:36:27 crappie syslogd 1.4.1#16ubuntu6: restart.

May 20 07:36:27 crappie exiting on signal 15
May 20 07:36:28 crappie syslogd 1.4.1#16ubuntu6: restart.


root@crappie:/dev # cat /var/log/messages | egrep "signal|restart"

May 20 07:40:03 crappie exiting on signal 15
May 20 07:40:04 crappie syslogd 1.4.1#16ubuntu6: restart.

May 21 07:36:25 crappie exiting on signal 15
May 21 07:36:26 crappie syslogd 1.4.1#16ubuntu6: restart.

May 22 07:36:29 crappie exiting on signal 15
May 22 07:36:30 crappie syslogd 1.4.1#16ubuntu6: restart.

May 23 07:36:30 crappie exiting on signal 15
May 23 07:36:31 crappie syslogd 1.4.1#16ubuntu6: restart.


```

---

### Post by JonahRowley on 2005-05-23
Is there anything out of place in the crontabs?

---

### Post by sfuhrman on 2005-05-23
[QUOTE=JonahRowley]Is there anything out of place in the crontabs?[/QUOTE]
 No, I checked the root cron jobs and cron.daily and didn't see anything unusual.  The only cron job I have added is a simple rsync script.  I also checked with rkhunter and chkrootkit and the system came up clean.  I am not running a GUI on this box, it is a pretty simple setup.  Only thing that is a bit different is that I am using ndiswrapper for the wireless NIC, but other than that it is a pretty normal system.

There is really nothing in the the messages or dmesg that point to a problem.  The weird thing is that the time remains fairly constant.

---

### Post by sfuhrman on 2005-05-23
I am going to throw a UPS on it when I get home tonight to rule out a bad power issue.  I am fairly certain it is not as all my other computers have been fine, but I suppose there is an off chance my neighbor fires up his electric welder or lead smelter every morning around 7:35  ;-)   I also wanted to add that this is not a laptop it is a normal P4 desktop.

---

### Post by sbooth on 2005-10-22
I'm having exactly the same problem - note that this thread was from a while ago.  Reboot at 07:35 each day, screens are black when I come to the machine in the evening and I have to power off and back on in order to get the machine to come alive again.  Not very satisfactory (perhaps I should just turn it off at night - but that isn't very compatible with overnight downloads!)

---

### Post by sbooth on 2005-10-23
No suggestions?  Original poster... did you solve it??

---

### Post by dpiven on 2005-10-26
The log messages do not necessarily indicate a system reboot; all that is happening here is that the syslogd daemon is being restarted.  Logrotate, for instance, will restart syslogd when it rotates stuff in /var/log, and will result in this message occurring whenever logrotate is scheduled to run.

If your system really IS being rebooted every day, you should be seeing a massive pile of messages in many of your logfiles, as well as never seeing an uptime over one day.  (Just for giggles, what is your uptime?)

---

### Post by sailorfej on 2007-01-29
Has this ever been resolved, I am seeing this on two other machines, 6.06.1.  The systems don't actually reboot, but on the local screen they appear to be hung on the boot screen with the last message reading "system messages backup", users have been hitting CTRL-ALT-DEL to restart the systems.  Although I believe that I have been able to ssh into the machines after one of these events, although I can't be sure as I am remote, and did not notice any issues when I logged in.

it is consistently happening at 7:35 am on both machines:

Jan 20 06:36:19 wsd004 -- MARK --
Jan 20 06:56:20 wsd004 -- MARK --
Jan 20 07:16:20 wsd004 -- MARK --
Jan 20 07:35:08 wsd004 exiting on signal 15
Jan 20 07:35:09 wsd004 syslogd 1.4.1#17ubuntu7: restart.
Jan 20 07:55:10 wsd004 -- MARK --
Jan 20 08:15:10 wsd004 -- MARK --
Jan 20 08:35:10 wsd004 -- MARK --

Any assistance here would be appreciated

---

### Post by n0mer on 2007-02-20
The same problem here: [http://ubuntuforums.org/showthread.php?t=245216](http://ubuntuforums.org/showthread.php?t=245216)

---

### Post by MJN on 2007-02-20
Guys - search the archives!! This is rapidly becoming eligible for FAQ #1!
 
Your machines aren't restarting, merely the syslogd service is (in order to free up the logs for rotation, and start afresh).
 
Mathew

---

### Post by theQmaster on 2008-01-02
Okay, okay the syslogd it restarts to rotate the logs but why at 7:35am! Someone should have an answer for this thing... on a second thought how do I change the rotation period ?
```

Jan  2 07:02:01 srv /USR/SBIN/CRON[25919]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Jan  2 07:15:01 srv /USR/SBIN/CRON[26644]: (root) CMD (/usr/local/awstats/tools/awstats_updateall.pl now >> /var/log/awstats.log)
Jan  2 07:17:01 srv /USR/SBIN/CRON[26653]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan  2 07:30:01 srv /USR/SBIN/CRON[26673]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jan  2 07:30:01 srv anacron[26697]: Anacron 2.3 started on 2008-01-02
Jan  2 07:30:01 srv anacron[26697]: Will run job `cron.daily' in 5 min.
Jan  2 07:30:01 srv anacron[26697]: Jobs will be executed sequentially
Jan  2 07:35:01 srv anacron[26697]: Job `cron.daily' started
Jan  2 07:35:01 srv anacron[26710]: Updated timestamp for job `cron.daily' to 2008-01-02
Jan  2 07:35:08 srv exiting on signal 15
```

---

### Post by MJN on 2008-01-02
Check /etc/crontab - it will define exactly when your hourly, daily, weekly and monthly cron jobs execute.

To change the syslog rotation frequency (although I have to ask why?) you would in this instance need to move the sysklogd cron job out of /etc/cron.daily/ and move it into one of the other predefined folders (weekly, monthly etc) or put it in /etc/cron.d/ suitably modified to execute at the required times (see man 5 crontab and/or search for info on 'crontab' for info how to do this).

If I were you I'd leave it alone, unless there is a specific reason you need it rotating more/less often.

Mathew

---

### Post by theQmaster on 2008-01-02
I have checklog sending me an email every morning telling me about a restart... See my prev. log. If is not a restart why the signal 15 ? Something is flaky, always happens at 7:35am.
I saw the syslogd in the daily crons.

Thanks a lot for replying MJN.

---

### Post by MJN on 2008-01-03
Post the exact contents of the e-mail and the rest of the log.
 
Mathew

---

### Post by Nevell on 2008-05-19
So, anyone fix this problem? Maybe its not a error?

*/var/log/messages*
> Apr 21 06:25:12 server exiting on signal 15
Apr 22 06:27:16 server exiting on signal 15
Apr 23 06:27:32 server exiting on signal 15
...
May 12 06:25:10 server exiting on signal 15
May 13 06:25:23 server exiting on signal 15
May 14 06:27:47 server exiting on signal 15
May 15 06:27:48 server exiting on signal 15
May 16 06:27:44 server exiting on signal 15
May 17 06:27:42 server exiting on signal 15
May 18 06:26:13 server exiting on signal 15
May 18 06:47:01 server exiting on signal 15

*/var/log/syslog*
> May 11 06:47:02 server exiting on signal 15
May 12 06:25:10 server exiting on signal 15
May 13 06:25:23 server exiting on signal 15
...
May 18 06:26:13 server exiting on signal 15
May 18 06:47:01 server exiting on signal 15

The same time on the every day. My time is GTM +3:00 (Moscow time). 

**P.S.** What is the -- MARK -- ?
> May 18 06:47:02 server syslogd 1.4.1#17ubuntu7: restart.
May 18 07:07:03 server -- MARK --
May 18 07:27:03 server -- MARK --
May 18 07:47:03 server -- MARK --
...
May 19 09:47:25 server -- MARK --
May 19 10:07:25 server -- MARK --
May 19 10:28:23 server syslogd 1.4.1#17ubuntu7: restart.

**P.P.S.** Ubuntu 6.06.01 LTS server

---

### Post by MJN on 2008-05-19
What problem? It's just your Syslog daemon (responsible for many system logs) restarting each day in order to free up the log for rotation/compression.
 
The --MARK-- is Syslog's way of telling you it is still alive and just doesn't have anything to log (otherwise you might start to think it has died if nothing new appears in the log).
 
Mathew

---

