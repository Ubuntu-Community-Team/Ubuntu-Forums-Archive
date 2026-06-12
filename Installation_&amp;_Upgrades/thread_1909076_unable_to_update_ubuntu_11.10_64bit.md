---
title: "unable to update ubuntu 11.10 64bit"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by kranthi457 on 2012-01-14
getting following error when updating ubuntu using sudo apt-get update

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

please advice..
Thanks

---

### Post by fantab on 2012-01-15
> **kranthi457 said:**
> getting following error when updating ubuntu using sudo apt-get update

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

please advice..
Thanks

Run the following in the Terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by Gstrazds on 2012-01-28
[B][FONT=Arial][SIZE=2]I want[/SIZE][/FONT][SIZE=2]ed to add this to the discussion... spent time looking for this solution in the forums; eventually found it in the help department [/SIZE]
[/B]

So anybody else needs to look no further... should you have this flavor of the problem

Glenn:popcorn:**Upgrading from Ubuntu 11.04**

 To  upgrade from Ubuntu 11.04 on a desktop system, press Alt+F2 and type in  "update-manager -d" (sans quotes) into the command box. Update Manager  should open up and display following message: "New distribution release  '11.10' is available. Click Upgrade and follow the on-screen  instructions".

---

