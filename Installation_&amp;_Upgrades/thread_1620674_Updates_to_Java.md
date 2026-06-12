---
title: "Updates to Java"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by AZinOH on 2010-11-13
I have two machines running 10.04. The older one dual-boots XP and was updated from 8.04 to 10.04 using the Update Manager. The newer one dual-boots Vista and had a clean install of 10.04. As far as I can see, both machines have the same update settings and the same repositories enabled. The older machine has received updates to Java which is now at v6 update 22. The newer machine has never been offered a Java update and is still at update 18. What would account for this process working differently on the two machines?. Thanks for any assistance.

---

### Post by howefield on 2010-11-13
Check the partner repository is enabled in the newer one.

System > Administration > Software Sources > Other Software tab.

---

### Post by AZinOH on 2010-11-13
> **howefield said:**
> Check the partner repository is enabled in the newer one.

System > Administration > Software Sources > Other Software tab.

Did as requested...no change yet.

---

### Post by howefield on 2010-11-13
> **howefield said:**
> Did as requested...no change yet.

Was the repository unchecked and now you have checked it ?

If so, reload your package list, with the terminal command

```
sudo apt-get update
```

and try update manager again.

---

### Post by AZinOH on 2010-11-13
> **howefield said:**
> Was the repository unchecked and now you have checked it ?

If so, reload your package list, with the terminal command

```
sudo apt-get update
```

and try update manager again.

Yes, that was the case. Did sudo apt-get update and tried update manager again, still no change.

---

### Post by AZinOH on 2010-12-04
On 12/1/2010 the newer machine finally got a Java update...to v6 update 20. Not going to complain, but still wondering why the two machines don't get the same updates.

---

