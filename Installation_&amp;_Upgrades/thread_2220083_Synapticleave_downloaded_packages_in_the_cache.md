---
title: "Synaptic:leave downloaded packages in the cache"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by cogset on 2014-04-26
I've checked the option in Synaptic to leave downloaded packages in the cache,nevertheless I'm seeing that when backing up my system with rsync,some .deb packages are deleted on the destination as they're evidently no longer in **/var/cache/apt/archives** on the source:if I'm understanding what's going on,there may be a limit for how many packages are kept there and/or for how long,is that the case?
Is the file *20archive* in **/etc/apt/apt.conf.d **
```
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
```
setting those limits? 
Can they be overridden to store packages indefinitely,and if so what could be the drawbacks,aside of the obvious usage of disk space?

---

### Post by vasa1 on 2014-04-26
> **cogset said:**
> ...
Is the file *20archive* in **/etc/apt/apt.conf.d **
```
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
```
setting those limits? 
Can they be overridden to store packages indefinitely,and if so what could be the drawbacks,aside of the obvious usage of disk space?
I guess you need to modify */etc/cron.daily/apt*. Setting all three to "0" may do what you want: "0" stands for disable rather than a value.

As for drawbacks, apart for the space issue which you've pointed out, I can't think of any.

---

### Post by cogset on 2014-04-27
Thanks,having read the **/etc/cron.daily/apt** file which you've pointed me to,looks like the suggested way to go about this is to create another preferences file **apt.conf.d/02periodic** in which to set the MaxAge and MaxSize custom values:

```

# This file understands the following apt configuration variables:
# Values here are the default.
# Create /etc/apt/apt.conf.d/02periodic file to set your preference.
```

---

