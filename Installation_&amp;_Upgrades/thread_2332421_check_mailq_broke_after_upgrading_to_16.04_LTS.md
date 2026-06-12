---
title: "check_mailq broke after upgrading to 16.04 LTS"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by lhpd1 on 2016-07-31
I'm not sure if I did something wrong during the upgrade to 16.04 LTS or what.

```
/usr/lib/nagios/plugins/check_mailq -w 2 -c 3
```

now fails with error

```
Use of uninitialized value $lines[0] in pattern match (m//) at /usr/lib/nagios/plugins/check_mailq line 330.Use of uninitialized value $lines[0] in pattern match (m//) at /usr/lib/nagios/plugins/check_mailq line 332.
Couldn't match /usr/bin/mailq output
```

I copied the first line of that error (figuring it to be where things start going wrong) into Google search, and later tried searching for "/usr/lib/nagios/plugins/check_mailq ubuntu 16.04 lts" in case someone else had run into problems getting check_mailq to work with 16.04 LTS, but no luck. I've got to be doing something all wrong. Could someone please point me in the correct direction? Thanks!

**Update:** My MTA is exim4 version 4.86.2-2ubuntu2, and

```
sudo -u nagios /usr/bin/mailq
```

gives no output.

---

