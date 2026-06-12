---
title: "Ubuntu 24.04 on btrfs with subvolume"
date: 2024-04-29
forum: Installation &amp; Upgrades
---

### Post by Silverfox_28 on 2024-04-29
Is there a procedure, a tutorial, to follow to install Ubuntu 24.04 on btrfs with subvolume?

---

### Post by #&amp;thj^% on 2024-05-03
If your still looking a good start with instructions found here: [https://blackstewie.com/posts/install-ubuntu-with-btrfs/](https://blackstewie.com/posts/install-ubuntu-with-btrfs/)

I definitely suggest adding a "@snapshots" with one note "/.snapshots" Keeps snapshots hidden.
Test each subvolume first before going hog wild. :)

---

### Post by kahupaa on 2024-05-06
The problem with new installer seems to be that it doesn't create any subvolumes. It was the same issue with 23.10 (default installer/subiquity). It just creates btrfs partition with mount point /. My testing about this has been one install on physical hardware and several VM installs of Ubuntu 23.10/24.04.  When choosing manual partitioning, seems like making encrypted volumes is missing as well.

---

### Post by #&amp;thj^% on 2024-05-06
> **kahupaa said:**
> The problem with new installer seems to be that it doesn't create any subvolumes. It was the same issue with 23.10 (default installer/subiquity). It just creates btrfs partition with mount point /. My testing about this has been one install on physical hardware and several VM installs of Ubuntu 23.10/24.04.  When choosing manual partitioning, seems like making encrypted volumes is missing as well.

I won't disagree the new installer needs some work, but at the live installer I'll quote a well known Dev here in UF.
> The new installer now makes it very visible that you can use a file to automate your install. Maybe that supports complex file system organization?

More on that here: [https://ubuntuforums.org/showthread.php?t=2495830](https://ubuntuforums.org/showthread.php?t=2495830)
I'm still working on a viable script that works for BTRFS, But nothing working yet....Grrr

---

