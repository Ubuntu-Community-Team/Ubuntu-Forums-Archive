---
title: "Cannot initialise Package Information"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by MauriceGoodf on 2008-06-12
Update Manager has failed with the following dialog:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Partyboi2 on 2008-06-12
Open a terminal (Applications>Accessories>Terminal) and try
```
sudo dpkg --clear-avail
```then 
```
sudo apt-get update
```

---

### Post by iaculallad on 2008-06-12
Try replacing your /var/lib/dpkg/status file with the status-old backup file located in the same directory and try re-updating:

Create a backup file first:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.date_today
```

Overwrite the original file with the old backup file:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Re-update:

```
sudo apt-get update
```

---

