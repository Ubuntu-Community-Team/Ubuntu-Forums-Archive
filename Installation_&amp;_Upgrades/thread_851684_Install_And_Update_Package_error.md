---
title: "Install And Update Package error"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by jean9120 on 2008-07-06
Hello, im getting an error from my package manager, when i open it, it displays this error 

E:Problem parsing dependency Depends, E:Error occurred while processing libgv-ruby (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

What could be wrong and how can i fix it?

---

### Post by iaculallad on 2008-07-06
Try the command below on your terminal:

```
sudo apt-get -f install
```

If that does not fix it, try the other command below:

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by jean9120 on 2008-07-06
The terminal comes up with this error for both codes:

E: Problem parsing dependency Depends
E: Error occurred while processing libgv-ruby (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

:(

---

### Post by iaculallad on 2008-07-06
> **jean9120 said:**
> The terminal comes up with this error for both codes:

E: Problem parsing dependency Depends
E: Error occurred while processing libgv-ruby (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

:(

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by jean9120 on 2008-07-06
it uninstalled them fine when i did that, but then when the update got to a vertain point the same message came up


E: Problem parsing dependency Depends
E: Error occurred while processing libgv-ruby (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by iaculallad on 2008-07-06
> **jean9120 said:**
> it uninstalled them fine when i did that, but then when the update got to a vertain point the same message came up


E: Problem parsing dependency Depends
E: Error occurred while processing libgv-ruby (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

What about doing the commands below on your terminal:

```
sudo mv /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages.old
```
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Rocket2DMn on 2008-07-06
Have you tried switching repositories from System->Administration->Software Sources ?  That should at least refresh the list files.

---

### Post by jean9120 on 2008-07-07
after doing all of that im getting this error now:

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

---

### Post by iaculallad on 2008-07-07
> **jean9120 said:**
> after doing all of that im getting this error now:

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

Just copy and paste this commands on your terminal: one-at-a-time

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update && sudo apt-get upgrade
```

---

