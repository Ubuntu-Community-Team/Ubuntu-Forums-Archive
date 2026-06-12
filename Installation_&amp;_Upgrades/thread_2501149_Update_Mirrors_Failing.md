---
title: "Update Mirrors Failing"
date: 2024-09-24
forum: Installation &amp; Upgrades
---

### Post by jcheong on 2024-09-24
Hi,

I have been getting the following for the past few days now.

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/noble/InRelease](http://sg.archive.ubuntu.com/ubuntu/dists/noble/InRelease)  Could not connect to sg.archive.ubuntu.com:80 (202.79.180.254), connection timed out
W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease](http://sg.archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease)  Unable to connect to sg.archive.ubuntu.com:http:
W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease](http://sg.archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease)  Unable to connect to sg.archive.ubuntu.com:http:
W: Some index files failed to download. They have been ignored, or old ones used instead.

How do we notify the owner that the mirror is down?

---

### Post by ian-weisser on 2024-09-24
Generally, you don't.

Mirrors go down regularly every day. Briefly. It might be synchronizing. It might be a maintenance window.

Or the mirror may have deliberately quit due to a policy change or new management. 

Admins don't really want to be peppered with dozens of "Hey, your mirror is down" messages every few hours when a mirror syncs. That's why they don't publish contact info.

Just try again later, or change your mirror.

---

### Post by Rubi1200 on 2024-09-25
Links are working for me, so I assume the mirrors are back up again.

Either try again or as **ian-weisser** suggested, change to a different mirror.

---

