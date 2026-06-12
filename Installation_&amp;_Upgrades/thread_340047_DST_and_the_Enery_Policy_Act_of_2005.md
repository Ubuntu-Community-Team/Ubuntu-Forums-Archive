---
title: "DST and the Enery Policy Act of 2005"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by mbobak on 2007-01-16
Can anyone confirm if the changes to Daylight Saving Time that are implemented by the US Energy Policy Act of 2005 are already in Ubuntu 6.10?

If you don't know what I'm talking about, see:
[http://en.wikipedia.org/wiki/Energy_policy_act_of_2005#Change_to_daylight_saving_time](http://en.wikipedia.org/wiki/Energy_policy_act_of_2005#Change_to_daylight_saving_time)

---

### Post by qntgeek on 2007-01-31
I saw this somewhere else and it seems to do the job of verifying your setup.

```
sudo zdump -v /etc/localtime |grep 2007
```

---

### Post by commonplace on 2007-02-02
> **qntgeek said:**
> I saw this somewhere else and it seems to do the job of verifying your setup.

```
sudo zdump -v /etc/localtime |grep 2007
```

Awesome. Looks like Ubuntu 6.10 is already set, then, 'cause mine displayed the proper changeover dates. Thanks for this information!

/Kevin

---

