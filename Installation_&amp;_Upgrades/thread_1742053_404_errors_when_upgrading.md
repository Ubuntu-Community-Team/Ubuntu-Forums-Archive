---
title: "404 errors when upgrading"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Trunkles on 2011-04-28
[SIZE=2]I tried to upgrade my maverick desktop machine as well as the server and got this...

```
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-common_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-gtk_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-draw_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-math_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 404  Not Found
```

I'm *really* confused now![/SIZE]

All ideas gratefully recieved. :)

---

### Post by ~Plue on 2011-04-28
looks like the mirror isn't ready yet.. try switching to the main server or just wait a little longer till the current one gets updated

edit: see post #3

---

### Post by ninja9578 on 2011-04-28
> **Trunkles said:**
> [SIZE=2]I tried to upgrade my maverick desktop machine as well as the server and got this...

```
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-common_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-gtk_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-draw_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-math_3.3.0-7ubuntu1_all.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb 404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 404  Not Found
```

I'm *really* confused now![/SIZE]

All ideas gratefully recieved. :)

Can you ping the server?

---

### Post by slooksterpsv on 2011-04-28
Can't ping the server, I just tried.

---

### Post by ninja9578 on 2011-04-28
> **slooksterpsv said:**
> Can't ping the server, I just tried.

Neither can I.  Im guessing the servers went down due to overuse.  That's common for any major software release.

---

### Post by Trunkles on 2011-04-28
Spot on! Thank you. I've changed to the main server and all is good.

---

### Post by Neotk on 2011-05-28
Guys, I'm having the same problem with launchpad gnome3 mirror.
I did not want to create a new thread since there are a lot of them in the search results. 
I see that you changed to the main server:
 
> **Trunkles said:**
> Spot on! Thank you. I've changed to the main server and all is good.

How did you do that? Sorry, I'm a complete idiot when facing linux issues.

(Trying to slowly move from Windows to Ubuntu, since Ubuntu is doing great!)

---

