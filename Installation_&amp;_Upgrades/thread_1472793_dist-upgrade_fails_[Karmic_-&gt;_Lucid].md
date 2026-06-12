---
title: "dist-upgrade fails [Karmic -&gt; Lucid]"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by ronzo on 2010-05-04
Today I was trying a dist-upgrade on a remote server.

Due to a problem with the hylafax-client package, dist-upgrade stopped. 

Another 'apt-get dist-upgrade' did not continue the upgrade process.

Even 'dpkg --configure -a' or 'apt-get -f install'  or 'apt-get upgrade' did not fix the problem  with the partially upgraded system.

Then I accidently rebooted the server and locked myself out - because the system did not come up again (maybe it dropped to a root shell after rebooting). 

Maybe i can boot up again with another kernel? I'll see...

What kind of procedure would you recommend me for this partially upgraded system? How can I fix it? (Setting sources back to karmic, upgrade again and afterwards to lucid) What would you recommend?

---

### Post by snowpine on 2010-05-04
'apt-get dist-upgrade' is not the correct command to upgrade from Karmic to Lucid.

Try 'do-release-upgrade' instead. :)

---

### Post by ronzo on 2010-05-04
Thanks! Did not know about do-release-upgrade...

Do you think it will fix my problem?

---

### Post by snowpine on 2010-05-04
If the only command you used was 'apt-get dist-upgrade' then you are still running Karmic. I do not really know what the problem is based on the limited information you've proviced, sorry. :( I have never used hylafax.

If stability is a concern, maybe wait a little while for the new Lucid release to settle down? If you hang out and read the forums, you'll get a heads-up on any major upgrade bugs.

---

### Post by ronzo on 2010-05-04
I've replaced all ocurrences of karmic with lucid in /etc/apt/sources.list, followed by an apt-get update. Then I did the dist-upgrade which was interrupted somewhere in the middle...

---

### Post by snowpine on 2010-05-04
> **ronzo said:**
> I've replaced all ocurrences of karmic with lucid in /etc/apt/sources.list, followed by an apt-get update. Then I did the dist-upgrade which was interrupted somewhere in the middle...

Gotcha, I believe that's how they do it in Debian... Ubuntu does not support that method, as far as I know. [Here is the official Ubuntu page on the topic]("http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29").

---

### Post by ronzo on 2010-05-04
I've upgraded several ubuntu machines over the past few years with the method described above and I've never experienced any problems...

---

### Post by snowpine on 2010-05-04
Cool, hopefully someone who's more experienced with that method will read this and offer up a solution. Sorry I wasn't much help. :)

---

### Post by ronzo on 2010-05-05
@snowpine: Thanks for your help! At least you pointed me to do-release-upgrade which I did not know before...

Someone has tips on how to fix the partially upgraded system?

---

### Post by ronzo on 2010-05-07
Is there someone around who knows what to do?

---

