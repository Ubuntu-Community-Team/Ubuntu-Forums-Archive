---
title: "Update to 20.04 query"
date: 2020-07-22
forum: Installation &amp; Upgrades
---

### Post by Philip_Edwards on 2020-07-22
I keep waiting for my laptop to tell me that there is an update to 20.04 update available but so far nothing.
Am I missing something?
Phil

---

### Post by mIk3_08 on 2020-07-22
You can try this command;
```
sudo do-release-upgrade -d
```

We will see if you will be able to force your system to upgrade to Ubuntu 20.04.

---

### Post by CatKiller on 2020-07-22
You won't get automatically notified of the next LTS from a previous LTS release until the first point release, to help shake out any bugs. I think that's scheduled for August. You can upgrade manually in the meantime with the command that mIk3_08 gave.

---

### Post by DigiAngel on 2020-07-30
August 6th:

[https://9to5linux.com/ubuntu-20-04-1-lts-focal-fossa-slated-for-release-on-july-23rd](https://9to5linux.com/ubuntu-20-04-1-lts-focal-fossa-slated-for-release-on-july-23rd)

also, adding the -d will usually get you to switch if you're on the non-server release gets you to a 19.10 upgrade.

---

### Post by ActionParsnip on 2020-07-30
The first point release is when it will be"seen" by the system. wait until a week on Friday and it'll be available to you

---

