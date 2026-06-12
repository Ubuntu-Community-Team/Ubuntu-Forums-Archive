---
title: "Problems with package manager"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by Semn on 2016-08-21
Hello, I cannot do anything with the package manager, at all. 

Please advise..

```
sem@sem-Latitude-E6430:~$ sudo apt-get remove --purge synaptic
[sudo] password for sem: 
Reading package lists... Error!
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:104
E: Unable to parse package file /var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-amd64_Packages (1)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```
```
sem@sem-Latitude-E6430:~$ sudo apt-get autoremove
Reading package lists... Error!
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:104
E: Unable to parse package file /var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-amd64_Packages (1)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
sem@sem-Latitude-E6430:~$
```

---

### Post by howefield on 2016-08-21
What is the output of 

```
cat /etc/apt/sources.list
```
and
```
ls -al /etc/apt/sources.list.d/
```

---

