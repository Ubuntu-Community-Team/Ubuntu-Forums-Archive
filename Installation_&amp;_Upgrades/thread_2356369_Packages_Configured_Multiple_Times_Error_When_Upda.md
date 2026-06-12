---
title: "Packages Configured Multiple Times Error When Updating"
date: 2017-03-22
forum: Installation &amp; Upgrades
---

### Post by Spencer_Thompson on 2017-03-22
Hello! I recently had to update Adobe Flash Player since the older versions were being blocked by my browser. It kept telling me it was already installed, so I purged the old version and installed the new one through APT. It still tells me it's out of date in my browser, but now I'm getting multiple errors when updating through the terminal. I'm using Firefox on Ubuntu 16.04. If anyone can help get rid of these errors, that would be awesome! Maybe even let me know how to update my flash player, but that's just icing on the cake.

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list.d/xenial-partner.list:4
```

---

### Post by deadflowr on 2017-03-22
The output is simply a warning that you have the same entry in the main sources.list file and in a special file named xenial-partner.list.
You can live with it or remove the file, as it is unneeded.
 
To do so, open a terminal and run
```
sudo rm /etc/apt/sources.list.d/xenial-partner.list
```
then run
```
sudo apt-get update
```
then run
```
sudo apt-get upgrade
```
post if any errors.

---

### Post by Spencer_Thompson on 2017-03-22
That did the trick. Good to know it wasn't anything serious.

---

