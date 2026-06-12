---
title: "[BUG] k3b doesn't run after installation"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by sque on 2006-09-29
After a fresh installation of Dapper Drake from the iso 6.06.1, I installed the k3b and I was I unable to start it (the k3b).

I ran it from console and reported permission denied at ~/.kde/some_path

I then checked out at my home folder and I noticed tha folders ~/.qt and ~/.kde belongs to user root rather my username. I chown(ed) this two folders to my username, and k3b now works :D

So, I think it should be checked:-k

---

