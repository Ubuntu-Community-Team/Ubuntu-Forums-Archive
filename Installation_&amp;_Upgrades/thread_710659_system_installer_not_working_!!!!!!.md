---
title: "system installer not working !!!!!!"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by wingit on 2008-02-28
system installer will not update keep getting same error ...


```

Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libenchant1c2a (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

---

### Post by taurus on 2008-02-28
What happens if you close that update window and run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by wingit on 2008-02-28
still getting same error 

:(```
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libenchant1c2a (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

---

