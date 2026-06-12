---
title: "Update manager wont restart update to 10.4 after broken download."
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Rahul_G on 2010-05-02
I started the upgrade to 10.4 from 9.10 through the update manager.
It started the update to 10.4. After downloading almost 95% of the update, it gave an error message of "could not download certain components. downloaded files will not be erased" and stopped the update.
I restarted the PC, and started the update manager again. But now it does not show any option of update to 10.4. how do i continue or resume the update process?

I just started using ubuntu about 15 days back. So, i am relatively new to this.

Thanks in advance for your help.

---

### Post by stephanski on 2010-05-02
I had the same problem when my internet went down part way through the download.
Rebooted the computer and found Update To 10.04 Install back in the Update Manager.
Continues on from package that failed to download.

---

### Post by madmax1735 on 2010-05-02
press "Alt+F2" 

and then type

```
update-manager -d
```


and then click away to new lucid


luck

---

### Post by Rahul_G on 2010-05-02
I tried your solution, but it does not work.
The Update Manager starts, checks for updates and the says " Your system is up to date ".
:(
Any other possibility...?
Or should i do a clean install by downloading the iso? (the 600 odd MB downloaded as part of update go waste)

---

