---
title: "I need the dapper beta1 iso image"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by bjacint on 2006-06-14
Hi everyone,

I really need the Kubuntu 6.06 dapper beta1 install image, but it has been removed from the official download page. (I need to perform a remote update.)
Does anyone has it somewhere?
Thank you so much in advance.

Yours,
Jacint

---

### Post by localzuk on 2006-06-14
Why do you specifically need the beta1 disc? I can't figure out why you would need it and could not use the dapper release disc?

---

### Post by bjacint on 2006-06-14
There's a machine 200 km away from me that have beta1 installed. It doesn't have internet connection, but I want to make an upgrade on it. So I install a beta1 on my computer (in vmware), do the upgrade, and then send the /var/cache/apt/archives directory by mail on a CD.
To install the beta1, I need to have it...

---

### Post by rcarring on 2006-06-14
Try this approach:

The target machine that runs Beta 1 needs to be upgraded to release.

If you provide the machine's user with the dapper alternate cd then the user can add this cd as a repository, remove the online repos, then do in adept the upgrade to the machine to release version without need for internet connection.

Provided always that the alternate cd repos contain all upgrades for the install on the machine.

---

