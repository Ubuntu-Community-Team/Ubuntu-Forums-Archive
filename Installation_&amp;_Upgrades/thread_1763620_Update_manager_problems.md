---
title: "Update manager problems"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by caricc on 2011-05-20
I am running 11.04 on an HP tx2 laptop. I have been able to perform updates until the last one. Then I get the following message when I try to use update manager or terminal to get updates or just to generally install a new program.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ftp.egr.msu.edu_pub_ubuntu_archive_dists_natty-updates_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Any help will be welcome. I performed the update from 10.10 online so I don't have the cd nor will I be able to download it. Not enough time to do so.

Thanks in advance.

---

### Post by Rubi1200 on 2011-05-20
Hi,
you can run these commands in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Should fix the problem.

Let us know if it works please.

---

### Post by caricc on 2011-05-21
yes, it did work. Thanks.

---

### Post by Rubi1200 on 2011-05-22
> **caricc said:**
> yes, it did work. Thanks.
Great news! Glad you got it sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page. It will also help others in a similar situation find a working solution.

Enjoy!

---

