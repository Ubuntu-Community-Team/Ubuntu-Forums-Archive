---
title: "Hash Sum Mismatch - Translation-en"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by jrlogicle on 2016-01-31
For a couple of weeks now, various repos have been returning a hash sum mismatch error when executing apt-get update. Sometimes switching mirrors works, sometimes switching distributions works. This seems to be a long-running and intermittent problem with various package archives, including archive.ubuntu.com.

One example: 
==> default: W
==> default: :
==> default: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en)  Hash Sum mismatch
==> default: W
==> default: :
==> default: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en)  Hash Sum mismatch
==> default: E: Some index files failed to download. They have been ignored, or old ones used instead.

It eventually clears up, but while it happens, scripts that automatically provision Ubuntu systems just fail until the problem resolves itself. (No, clearing out the apt-cache and resetting doesn't work).

Tried today with: trusty, vivid and wily. All failing on brand new installations. Today's issue was translation. Last week it was security updates.

There have been posts about this periodically for a couple of years now. The problem "clears itself up" and is tagged as "solved", but clearly this is a recurring issue for many users.

---

### Post by ajgreeny on 2016-02-01
You may find you can overcome this problem and speed up the **apt-get update** reload by removing non-English translations by adding line
```
Acquire::Languages "none";
```
to /etc/apt/apt.conf.d/00aptitude

It makes no difference to the repos that are used, just the non-English translations that are available for them.  I have been using this in my configuration for a couple of years with no problems at all, so it is worth a try , I think.

---

