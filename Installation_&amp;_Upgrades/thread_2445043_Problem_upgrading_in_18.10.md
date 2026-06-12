---
title: "Problem upgrading in 18.10"
date: 2020-06-08
forum: Installation &amp; Upgrades
---

### Post by reedcook on 2020-06-08
this is an error i get when using this command lines.


E: Malformed entry 59 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.


im using ubuntu 18.10 as well.  any way to fix it?

---

### Post by ajgreeny on 2020-06-08
We can  not help you to solve this problem apart from telling you to upgrade or clean install to a fully supported version of Ubuntu; I would recommend 20.04.

The reason for that error message is that repositories for 18.10 were closed back in August 2019, moved to an EOL server as archives, and will no longer supply any further upgrades, meaning a system upgrade, or better clean install, is essential for security reasons.

---

### Post by ActionParsnip on 2020-06-08
What is the output of:
```

cat -n /etc/apt/sources.list

```
As stated earlier, even if you sort it there are no packages for your release. It's like searching for updates for Windows XP. They don't exist
I suggest you do a final full backup, Wipe the install off and do a clean install of Focal (Ubuntu 20.04) and then restore your user data from your backups. You will then have support for 5 years

---

