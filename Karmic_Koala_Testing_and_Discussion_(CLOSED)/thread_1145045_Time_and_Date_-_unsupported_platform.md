---
title: "Time and Date - unsupported platform ?"
date: 2009-05-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-05-01
Using the latest Karmic kernel 2.6.30-1 (i686) on an old Athlon 900MHz PC. If I go to System-Admin-Time and Date, I get 'The platform you are running is not supported by this tool' (see attached).
Should I raise a bug report ?

---

### Post by autocrosser on 2009-05-01
The answer is Yes---I get the same thing---I'm almost heading to work or I would---someone forgot to update the distro list ;)

If you post the link to the report I will confirm it during my break....

---

### Post by Kevbert on 2009-05-01
The bug report is [[COLOR="Red"]370366[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/370366"). Please can you confirm this bug. Thanks.

---

### Post by taavikko on 2009-05-01
> **Kevbert said:**
> The bug report is [[COLOR="Red"]370366[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/370366"). Please can you confirm this bug. Thanks.

I confirmed it, but at this early in the cycle when their sync with Sid is still iin progress, bug reports IMO is futile.

---

### Post by autocrosser on 2009-05-01
I added a comment---if you look at the drop-down---nothing newer than 8.04 is "supported" !!!!  :lolflag:

---

### Post by Kevbert on 2009-05-01
Thanks guys.

---

### Post by taavikko on 2009-05-01
apport-collect is nice tool :)

---

### Post by davideotape on 2009-05-01
I have the same problem with users and groups. I'll add a comment to the bug :)

---

### Post by ronacc on 2009-05-01
I'm also getting that on users and groups , I'll add a comment also .

---

### Post by Kevbert on 2009-05-01
> **taavikko said:**
> apport-collect is nice tool :)

I've enabled apport and rebooted. How do I get it to work with this problem ?

---

### Post by taavikko on 2009-05-01
> **Kevbert said:**
> I've enabled apport and rebooted. How do I get it to work with this problem ?

```
man apport-collect
```

Or for reference: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by autocrosser on 2009-05-01
So--if more than Time & Date are affected---there must be a config that shows "supported" distros--Could this be a build farm issue?

---

### Post by Kevbert on 2009-05-01
```
apport-collect 370366
```
Reply
```
Bug title: [Karmic] Time and Date - platform not supported
Ignoring task https://api.edge.launchpad.net/beta/ubuntu
Uploading additional information to Launchpad bug...
   short text data...
Traceback (most recent call last):
  File "/usr/bin/apport-collect", line 143, in <module>
    except launchpadlib.errors.HTTPError, e:
NameError: name 'launchpadlib' is not defined
```
Am I doing something wrong ?

---

### Post by dinxter on 2009-05-02
think this comes from system-tools-backends, "/usr/share/system-tools-backends-2.0/scripts/Utils/Platform.pm" which seems to only go up to Hardy, which meta maps all the way back to feisty! seems to have been that way for the intrepid and jaunty releases too so i'm not sure why its suddenly popped up the unsupported distro now

---

### Post by dinxter on 2009-05-02
seems "/var/cache/system-tools-backends/detected-platform" is empty which might be something to do with it, sadly my perl isn't good enough :) so i've not sure where exactly this is checked/set

---

### Post by davideotape on 2009-05-06
Seems this bug was fixed today.

---

