---
title: "Disable third-party repos from the CLI"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by everythingsround on 2010-11-05
I am looking to upgrade a box of mine using command line only.  I am going from 10.04 to 10.10 and have changed all instances of lucid to maverick within the sources.list file but now I don't want to continue until I can be safe to upgrade by disabling the third-party repos.  

How can I disable these using the command line?  Should I just move the sources.list.d folder? Any other ways I'm missing?

Thanks for any help and clarification.

---

### Post by oldos2er on 2010-11-05
Instead of moving sources.list.d/, I would just rename it to 10.04.sources.list.d for example. Either way would work.

---

### Post by everythingsround on 2010-11-05
> **oldos2er said:**
> Instead of moving sources.list.d/, I would just rename it to 10.04.sources.list.d for example. Either way would work.

Cool idea, Thanks! ~2hr countdown.  Let's hope it is a smooth transition. 

Thanks, again.

---

### Post by snowpine on 2010-11-05
Curious if you read the [Upgrade Notes]("https://help.ubuntu.com/community/MaverickUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29"), as changing "lucid" to "maverick" in your sources.list file is definitely **not** the recommended method...

---

### Post by everythingsround on 2010-11-05
> **snowpine said:**
> Curious if you read the [Upgrade Notes]("https://help.ubuntu.com/community/MaverickUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29"), as changing "lucid" to "maverick" in your sources.list file is definitely **not** the recommended method...

I did, but I wouldn't have thought that was the preferred method.  Oh well, what's done is done. 

Thanks for the tip, but I hope it works either way.

---

