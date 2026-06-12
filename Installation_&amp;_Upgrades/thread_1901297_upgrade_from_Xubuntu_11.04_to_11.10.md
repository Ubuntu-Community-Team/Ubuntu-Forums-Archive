---
title: "upgrade from Xubuntu 11.04 to 11.10"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by bedwyr on 2011-12-28
Hello,

Im'going to upgrade my Xubuntu. Reading the release notes, i see this paragraph:
Ubuntu 11.10 has migrated away from /var/run, /var/lock and /dev/shm and now uses /run, /run/lock and /run/shm instead (respectively). While the Ubuntu AppArmor packages and shipped policy have been adjusted for this, custom policy may need to be updated. The following may be used to aid in migration (it allows both the old and the new paths):
> $ sed -i -e 's#/var/run#/{,var/}run#' -e 's#/var/lock#/{run,var}/lock#' -e 's#/dev/shm/#/{dev,run}/shm/#' <profile> 

When I'm executing this command, bash returns:
bash : syntax error near unexpected symbol « newline »

Does anybody know how to fix this command ?

Thanx

---

### Post by hsoulen on 2011-12-28
Hi,

Just to be sure when you executed this command you replaced "<profile>" with your custom apparmor profile correct?

```
$ sed -i -e 's#/var/run#/{,var/}run#' -e 's#/var/lock#/{run,var}/lock#' -e 's#/dev/shm/#/{dev,run}/shm/#' <profile>
```

I will have a look at it otherwise.

Cheers,

Hank

---

### Post by bedwyr on 2011-12-28
> **hsoulen said:**
> 
Just to be sure when you executed this command you replaced "<profile>" with your custom apparmor profile correct?



No :???:, I just execute this with "<profile>". It must explain why :)

How do I find my custom apparmor profile ??

Thanks for your help

---

### Post by hsoulen on 2011-12-28
I am not 100% confident but I believe this would be your actual user profile e.g. "~hsoulen" or "/home/hsoulen" (contains your path variables).

But to be perfectly honest unless you have added application profiles for apparmor in the past due to issues with secure linux not correctly executing an application you probably do not need to perform this step at all.

Cheers,

Hank

---

### Post by bedwyr on 2011-12-28
Yes, maybe it's not important .. I don't know.

I tried to replace <profile> by my user account ~/user or /home/user but it does not work ("not a regular file").

---

