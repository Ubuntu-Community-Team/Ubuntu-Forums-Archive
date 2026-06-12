---
title: "Unable to run Update (of any variant), says &quot;header&quot; information missing"
date: 2018-04-21
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2018-04-21
I first became aware of this issue when I noticed a circular, red icon with a white horizontal line through the middle, sitting in the top task bar near the clock.
It said to run Package Manager or apt-get, to find out what was causing the error.

I've attached the results in a text file of what I got when trying to run sudo apt-get update.

---

### Post by oldos2er on 2018-04-21
Hash sum mismatch and mergelist errors can usually be fixed with the solution posted here: [https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error](https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error)

I would remove the repositories that give a 404 error.

---

### Post by netsurfau on 2018-04-25
G'day Oldos2er,

I followed the suggested fix on the linked page and it seemed to fix the issue I
was experiencing. But, it seems to have found another problem.

When running apt-get update it stopped with giving the following error.

W: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

Cheers
Netsurf

---

