---
title: "Last Update messed up computer"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by mhbell on 2010-12-03
The last update of a few days ago messed up the update manager. here is the error that I get. I do not have the time to hunt for bug reports to report this and don't know how anyway. maybe someone else can do it.


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Rubi1200 on 2010-12-03
Try running the following commands from the terminal:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Post back with errors please.

---

### Post by sikander3786 on 2010-12-03
Make sure you are not running out of space on your Ubuntu partition.

```
df -h
```

If the above commands mentioned by Rubi1200 don't solve the issue, try reverting to an older dpkg/status file.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update
```

If the above one's don't help, try this.

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

If this doesn't help either, post the output of Rubi1200's commands and also this one.

```
sudo apt-get check
```

---

