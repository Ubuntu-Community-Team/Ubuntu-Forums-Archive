---
title: "Problem parsing dependency Depends E: Error occurred while processing python-glade2 ("
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by shadow00 on 2010-12-27
hello 
i have some problems
can anyone help me....?

```
E: Problem parsing dependency Depends
E: Error occurred while processing python-glade2 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

---

### Post by karthick87 on 2010-12-27
Post the output of,
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sikander3786 on 2010-12-27
If the above doesn't solve your problem, try using an older /dpkg/status file.

Applications > Accessories > Terminal:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mshenrick on 2011-02-19
> **sikander3786 said:**
> If the above doesn't solve your problem, try using an older /dpkg/status file.

Applications > Accessories > Terminal:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
``````
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
``````
sudo apt-get install -f
``````
sudo apt-get update && sudo apt-get upgrade
```

worked great! thanks!

---

### Post by Machiavelli on 2011-10-22
> **sikander3786 said:**
> If the above doesn't solve your problem, try using an older /dpkg/status file.

Applications > Accessories > Terminal:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
``````
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
``````
sudo apt-get install -f
``````
sudo apt-get update && sudo apt-get upgrade
```

You sir, are a genius!

Thank you. :guitar:

---

