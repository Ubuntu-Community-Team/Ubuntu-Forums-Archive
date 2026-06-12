---
title: "Update from 17.04 to 18.04 by Reinstalling"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by kodingkoning on 2019-06-03
I am currently running an installation of Ubuntu 17.04. I want to update it to 18.04. Because I'm running 17.04, I can't update through the updater. I am also running into issues with "sudo apt-get update", so that's preventing me from updating that way.

I am running Ubuntu as a partition alongside Windows with GNU GRUB.

I would like to uninstall this version and install the latest version. How can I do this?

I have everything backed up in my Ubuntu partion, so I am anticipating losing all the information there, but I don't want to lose Windows data, if possible.

---

### Post by Bashing-om on 2019-06-03
kodingkoning; Hello
> 
End-Of-Life is when security updates and support for an Ubuntu release stop, see 
               [https://help.ubuntu.com/community/EOL](https://help.ubuntu.com/community/EOL) for more info. Looking to upgrade from an EOL release? See 
               [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


You re looking at a lengthy process and a lot of bandwidth:
17.04 -> 17.10 (EOL) -> 18.04
A fresh install of 18.04; choose the install method "something else" and point the installer to the partition that is presently occupied by the 17.04 install.
To know the target:
```

sudo parted -l

```

[INDENT]my bit to try and help
[/INDENT]

---

### Post by kodingkoning on 2019-06-11
Hi Bashing-om,

Thank you for the info about EoL releases. Based on a previous thread I started, I concluded that it would be better for me to go with a clean install because I was running into many issues with the upgrades.

Would there be a way, say, to create a new installation in the partition that already exists without dealing with the 17.04 issues?

Thanks.

---

### Post by tea for one on 2019-06-11
> **kodingkoning said:**
> Would there be a way, say, to create a new installation in the partition that already exists without dealing with the 17.04 issues? Thanks.

Yes, it was mentioned in Bashing-om's post > A fresh install of 18.04; choose the install method "something else" and point the installer to the partition that is presently occupied by the 17.04 install.

I would also advise that you have full back-ups of your Widows partitions before installing 18.04 where 17.04 used to live.

Back-ups and the confidence in restoring back-ups are essential, not only for peace of mind but also for good housekeeping.

---

