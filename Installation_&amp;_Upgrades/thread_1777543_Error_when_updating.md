---
title: "Error when updating?"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by ddarsow on 2011-06-07
I get an error when trying to run update manager or Synaptic - same thing from Ubuntu Tweak as well.... I also tried to update via terminal

```
sudo apt-get update
```

and got the following error:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Running 11.04 x64, been exclusively Ubuntu since 8.04 and never encountered this before.

---

### Post by wildmanne39 on 2011-06-07
> **ddarsow said:**
> I get an error when trying to run update manager or Synaptic - same thing from Ubuntu Tweak as well.... I also tried to update via terminal

```
sudo apt-get update
```

and got the following error:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Running 11.04 x64, been exclusively Ubuntu since 8.04 and never encountered this before.

Hi, try this
```
sudo rm -r /var/lib/apt/lists/* -vf

```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ddarsow on 2011-06-08
> **wildmanne39 said:**
> Hi, try this
```
sudo rm -r /var/lib/apt/lists/* -vf

```
```
sudo apt-get update && sudo apt-get upgrade
```

That did it.
Thanks!

---

### Post by wildmanne39 on 2011-06-08
> **ddarsow said:**
> That did it.
Thanks!Hi, your welcome.:)

---

