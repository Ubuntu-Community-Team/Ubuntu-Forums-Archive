---
title: "Upgrading, Fonts - all text is now boxes"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by PeterRooke on 2007-11-18
I've just tried to upgrade, and found that all the operating system GUI text is now small boxes.  I can still open a shell window and have tried a few things with the command line package manager (apt), but nothing seems to work.

Any idea's - I think I am looking at backing up the data and then re-installing, but I really could do without the hassle.

---

### Post by bapoumba on 2007-11-18
Please try:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
And paste the error if you have any (many times, these boxes mean you have not fully upgraded and miss some packages), along with your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by slittle on 2007-12-28
I had the same problem, and running the sudo apt-get update and
sudo apt-get dist-upgrade fixed the problem.

Thanks a lot for the info.:)

---

