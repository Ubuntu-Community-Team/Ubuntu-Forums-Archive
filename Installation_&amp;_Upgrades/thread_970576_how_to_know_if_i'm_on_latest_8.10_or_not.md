---
title: "how to know if i'm on latest 8.10 or not?"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Bashar &quot; on 2008-11-04
i installed 8.10 when it was beta, and my system was doing updates during the past few days, i want to know if i'm on the latest 8.10 or still on 8.10 beta ?

which file to check?

bashar@bashar-laptop:/etc$ more lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

does this mean i'm on latest version of ubuntu no longer on beta ?

Thanks

---

### Post by snowpine on 2008-11-04
Use the Update Manager or 'sudo apt-get upgrade' and you will be up to date with the current release version.

---

### Post by RequinB4 on 2008-11-04
run:

```

cat /etc/issue

```

if it doesn't have (develoment release) then you have the real one.

---

### Post by Bashar &quot; on 2008-11-04
> **RequinB4 said:**
> run:

```

cat /etc/issue

```

if it doesn't have (develoment release) then you have the real one.
thanks guys, it seems it ugpraded to latest :)

---

