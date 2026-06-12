---
title: "Malformed Release File?"
date: 2009-01-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by blazemore on 2009-01-04
```

W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```

When I try to use update-manager -d

Any ideas?

---

### Post by autocrosser on 2009-01-04
Garbled in transit---try again later......my best guess.  Are you using the main repo or a mirror?

---

### Post by blazemore on 2009-01-05
I was using a mirror, and got that error.
I switched to Server for UK and still get it.

---

### Post by autocrosser on 2009-01-05
Try the main repo & see if it still happens....

---

### Post by vikrant82 on 2009-01-05
Before starting upgrade comment out any lines containing "partner". Most probably these ones: 

```
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
```

Hope that helps.

---

### Post by blazemore on 2009-01-05
Tried both of these suggestions.
I put in a vanilla Jaunty sources.list and ran
```
sudo aptitude full-upgrade -y
```

I'm not at home now, so I'll see if it works when I get back.

---

### Post by Gina on 2009-01-05
I always use the main server for development testing as the mirrors are up to a week out of date.  This applies to the **gb** server for the UK.

---

