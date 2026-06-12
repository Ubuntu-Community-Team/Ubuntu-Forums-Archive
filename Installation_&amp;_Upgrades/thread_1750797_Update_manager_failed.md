---
title: "Update manager failed"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by sgtryan on 2011-05-05
Please help me, I was trying to open the Update Manager and this popped up...

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'"

---

### Post by orangep on 2011-05-07
Yes, I'm getting the same bug. 
I did a clean install: save data, and blitz the disk. Hardware=Compal HE81
notebook computer, Intel Core2 Duo, 1.5 GB ram, 80 GB disk.

The installation from the CD worked, and now, while trying to install something more to make the system actually usable (why no distribution DVD? especially with NFS on it?), I get:

> apt-get update

produces:
...
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 1,550 kB in 40s (38.3 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Then, attempts to install anything fail:

# apt-get install dselect
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

And that is the end of Ubuntu version 11.04

Why is this stuff released before debugging?

---

### Post by matt_symes on 2011-05-07
Hi

For both of you.

Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen. This is normal.

Then type 

```
sudo apt-get update
```

If it complains about a folder called /var/lib/apt/lists/partial type being missing

```
sudo mkdir /var/lib/apt/lists/partial
```

Then type this again

```
sudo apt-get update
```

Kind regards

---

### Post by orangep on 2011-05-07
Yes! thank you.

sudo rm /var/lib/apt/lists/* -vf

gets rid of the bad file.

---

