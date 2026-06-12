---
title: "Can't upgrade to 10.04: 'kubuntu-desktop' marked for removal"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by rocketman768 on 2010-05-24
Can't upgrade from 9.10 to 10.04. First, I had to upgrade from 9.04 to 9.10, and that hosed my internet connection, so I had to download the alternate cd and run the update off the cd. However, soon into the install, it comes up with the error:

Could not calculate the upgrade. The package 'kubuntu-desktop' is marked for removal but it is in the removal blacklist.

After some searching, it seemed that the error came from having 'ubuntu-desktop' and 'kubuntu-desktop' installed at the same time. I removed it by "sudo aptitude remove ubuntu-desktop", but I still have the exact same error. After checking the /var/log/dist-upgrade/main.log, I find the following messages: DEBUG none of the '['ubuntu-desktop', 'kubuntu-desktop', 'xubuntu-desktop', ubuntustudio-desktop', 'ichthux-desktop', 'mythbuntu-desktop', 'kubuntu-netbook']' meta-pkgs installed
DEBUG guessing 'ubuntu-desktop' as missing meta-pkg

However, this doesn't make any sense to me since 'kubuntu-desktop' is clearly marked as installed in aptitude. Any ideas here?

---

