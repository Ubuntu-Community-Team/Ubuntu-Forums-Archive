---
title: "Ubuntu 12.04LTS update problem."
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by Mads_Mikkel_Trsl on 2014-08-23
Hi guys,

In the last wek or so, I got this message when the system tried to get updates:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da, E:Pakkelisterne eller statusfilen kunne ikke tolkes eller åbnes.

Any ideas as to what might cause - or more interesting - solve this?

Mads, DK (Not an expert user of Ubuntu)

---

### Post by ajgreeny on 2014-08-23
One of the files in the folder shown in the error is corrupt for some reason, so run commands ```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```
The first command will probably show an error about not being able to remove the **partial** folder which you can ignore, but with luck your updates will now work OK.

---

### Post by Mads_Mikkel_Trsl on 2014-08-25
That seems to have solved it :-)

Thank you!

---

