---
title: "Unable to open Ubuntu Software Center and unable to do software updates"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by tlotr on 2013-03-23
Hi All,

I am getting this error message when I try to do software update. Also there is an [X] icon on the gnome bar at top. I have attached the error message in the thread.

Please help me in resolving this issue.

I have checked the path which shows in the error /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_universe_i18n_Translation-en this file exists and I am not sure why I am getting this error message.

---

### Post by ManamiVixen on 2013-03-23
Refresh the lists again. with the update command. There are instances where the lists won't update properly but will a second time.

---

### Post by tlotr on 2013-03-23
Hi ManamiVixen,

Thanks for the reply. I've tried it again but still getting the same error message.

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
gregory@linux:~$ 

```

---

### Post by tlotr on 2013-03-23
Hi All,

The issue has been resolved. Got the resolution from this thread.

[http://ubuntuforums.org/showthread.php?t=2074326](http://ubuntuforums.org/showthread.php?t=2074326)

---

