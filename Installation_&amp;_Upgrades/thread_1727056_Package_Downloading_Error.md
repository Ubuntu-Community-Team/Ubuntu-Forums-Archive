---
title: "Package Downloading Error"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by interglobe07 on 2011-04-12
When using an Update Manager, I encountered the following error message, and after that all system upgrade related programs stopped working properly. I guess this is because of changes in headers in the server. But the problem is that I do not know how to synchronize the directory and headers.

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Can anyone teach me how to resolve this problem?

Best

---

### Post by plucky on 2011-04-12
> **interglobe07 said:**
> When using an Update Manager, I encountered the following error message, and after that all system upgrade related programs stopped working properly. I guess this is because of changes in headers in the server. But the problem is that I do not know how to synchronize the directory and headers.

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Can anyone teach me how to resolve this problem?

Best


Remove the file from a terminal with ```
cd /var/lib/apt/lists
sudo rm archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
```

Then run ```
sudo apt-get update
``` will download a new version.


Good Luck

---

### Post by interglobe07 on 2011-04-12
Thanks for your suggestion.
It did not work, but I resolved this problem.

Best

---

### Post by plucky on 2011-04-12
> **interglobe07 said:**
> Thanks for your suggestion.
It did not work, but I resolved this problem.

Best

And your solution was?

This might help someone else when they search the forum and come across your thread.

---

### Post by interglobe07 on 2011-04-12
Hi,

Thanks for your interest.
I also reported this error as a system bug.
One developer suggested me the following, and it worked well for me:

sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*; sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists; sudo mkdir /var/lib/apt/lists/partial
LANG=C;sudo apt-get clean; LANG=C;sudo apt-get autoclean
LANG=C;sudo apt-get update
sudo dpkg --clear-avail; sudo dpkg --configure -a
LANG=C;sudo apt-get install -f
LANG=C;sudo apt-get update
LANG=C;sudo apt-get dist-upgrade

I hope this syntax would be helpful.

Best,

---

### Post by hmnhf on 2011-05-03
thanks, it works :D

---

