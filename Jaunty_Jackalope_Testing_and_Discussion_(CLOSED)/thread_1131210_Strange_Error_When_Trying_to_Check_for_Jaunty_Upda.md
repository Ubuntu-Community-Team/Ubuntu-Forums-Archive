---
title: "Strange Error When Trying to Check for Jaunty Updates"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-04-20
When I attempted to check for updates..I was presented with "E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory"

Anyone have any ideas? Would changing the server help any?

---

### Post by psyke83 on 2009-04-20
> **sox fan Matt said:**
> When I attempted to check for updates..I was presented with "E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory"

Anyone have any ideas? Would changing the server help any?

It means another application is accessing your dpkg database, or the update checker didn't get root access.

This problem can occur typically when the update check runs and you have Synaptic open.

---

