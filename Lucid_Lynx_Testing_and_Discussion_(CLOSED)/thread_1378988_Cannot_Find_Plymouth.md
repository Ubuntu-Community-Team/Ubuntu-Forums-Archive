---
title: "Cannot Find Plymouth"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-01-12
Lucid Lynx will start boot process, go's to CANNOT FIND PLYMOUTH
Then hangs before Splash screen in 3 different kernals 6,9 and 10.

So far have not found any fix: Is there any idea's out there?

---

### Post by cykotiktek on 2010-01-12
I have the same error but for some reason mine boots normally hopefully someone can shed some light on this

---

### Post by VMC on 2010-01-12
I get it too, and have for a while now. I don't think I have Plymouth fully installed. What shows when you search for it?:

```
$ aptitude  search plymouth
p   libplymouth-dev                 - graphical boot animation and logger - deve
**[COLOR="Red"]i[/COLOR]** A libplymouth2                    - graphical boot animation and logger - shar
p   plymouth                        - graphical boot animation and logger - main

```

Looks partially installed.

---

### Post by cykotiktek on 2010-01-12
p   libplymouth-dev                 - graphical boot animation and logger - deve
i A libplymouth2                    - graphical boot animation and logger - shar
p   plymouth                        - graphical boot animation and logger - main

---

### Post by dino99 on 2010-01-12
have had some problems to boot too, but today have spend some free time on it:
- remove/purge the old things like usplash, *splash
- remove/purge plymouth

run bleachbit to clean up the system

then install plymouth

now no problemo, all fine :)

---

### Post by jfernyhough on 2010-01-12
Does this mean xsplash is a gonner now?

After all that effort getting it to work in Karmic...

---

### Post by VMC on 2010-01-12
> **jfernyhough said:**
> Does this mean xsplash is a gonner now?

After all that effort getting it to work in Karmic...

I don' think so. I haven't done anything with the repos and both xsplash & usplash are insalled:

```
Package: xsplash
State: installed
Automatically installed: no
Version: 0.8.5-0ubuntu1

Package: usplash
State: installed
Automatically installed: no
Version: 0.5.51

```

---

