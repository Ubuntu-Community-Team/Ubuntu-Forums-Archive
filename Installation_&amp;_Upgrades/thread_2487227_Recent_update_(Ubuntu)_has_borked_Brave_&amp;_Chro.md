---
title: "Recent update (Ubuntu) has borked Brave &amp; Chrome"
date: 2023-05-27
forum: Installation &amp; Upgrades
---

### Post by Daveski17 on 2023-05-27
The last update has seriously compromised Chrome and Brave's ability to render. How do I fix this? Firefox is fine. Thanks.

---

### Post by QIII on 2023-05-27
Which release are you running, and what flavor?

---

### Post by Daveski17 on 2023-05-27
Ubuntu Jammy Jellyfish. I've tried uninstalling and reinstalling Chrome, but to no avail. I've read this has happened to people. Both Chrome and Brave were installed via the Terminal.

---

### Post by ian-weisser on 2023-05-27
Folks receive different upgrades at different times, so we don't know what your "last update" contained. Your /var/log/apt logs have that information.

---

### Post by Daveski17 on 2023-05-28
> **ian-weisser said:**
> Folks receive different upgrades at different times, so we don't know what your "last update" contained. Your /var/log/apt logs have that information.

OK thanks mate. So, where are those logs exactly and I'll try to post them. Cheers.

---

### Post by makitso on 2023-05-28
This happened, to me, with my Brave browser.  After the normal apt update (see below), the brave profile was completely replaced with new files.
I did have the Brave browser open at the time of update but I have done that many times before.

Start-Date: 2023-05-18  04:41:30
Commandline: aptdaemon role='role-commit-packages' sender=':1.122'
Upgrade: cups-filters:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), brave-keyring:amd64 (1.13, 1.14), libfontembed1:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), cups-filters-core-drivers:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), cups-browsed:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), brave-browser:amd64 (1.51.114, 1.51.118), libcupsfilters1:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2)
End-Date: 2023-05-18  04:41:44

---

### Post by ian-weisser on 2023-05-28
Might be [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/2020604](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/2020604), which affects both Brave and Chrome.

---

### Post by Daveski17 on 2023-05-28
> **makitso said:**
> This happened, to me, with my Brave browser.  After the normal apt update (see below), the brave profile was completely replaced with new files.
I did have the Brave browser open at the time of update but I have done that many times before.

Start-Date: 2023-05-18  04:41:30
Commandline: aptdaemon role='role-commit-packages' sender=':1.122'
Upgrade: cups-filters:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), brave-keyring:amd64 (1.13, 1.14), libfontembed1:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), cups-filters-core-drivers:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), cups-browsed:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2), brave-browser:amd64 (1.51.114, 1.51.118), libcupsfilters1:amd64 (1.28.15-0ubuntu1, 1.28.15-0ubuntu1.2)
End-Date: 2023-05-18  04:41:44

Thanks for the info.

---

### Post by Daveski17 on 2023-05-28
> **ian-weisser said:**
> Might be [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/2020604](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/2020604), which affects both Brave and Chrome.

OK, cheers for the info mate. I'm hoping for an update fix sometime in the future. Meanwhile Firefox is holding its own, I forgot how good Fx was. :o

---

### Post by ajgreeny on 2023-05-28
> **Daveski17 said:**
> OK, cheers for the info mate. I'm hoping for an update fix sometime in the future. Meanwhile Firefox is holding its own, I forgot how good Fx was. :o
I have almost never moved away from Firefox which is my default browser on my Xubuntu 22.04.
I do not use the snap version, in fact I have removed the complete snap infrastructure, eg snapd, etc, 
from my systems and installed Firefox using the .tar.gz archive which I have extracted simply into ~/Downloads  as I'm the sole user on the machine. If there were other users I would have extracted it into /opt as we're supposed to do.

It all works just the same as it used to when it was a .deb installed version and notifies me when a new version is available to download. 

I occasionally use chromium from a ppa, never the snap, and apart from my Android tablet where it used to be my browser, I've never used Chrome, and even on Android now I never use Chrome, having switched to Brave.

---

### Post by Daveski17 on 2023-05-28
> **ajgreeny said:**
> I have almost never moved away from Firefox which is my default browser on my Xubuntu 22.04.
I do not use the snap version, in fact I have removed the complete snap infrastructure, eg snapd, etc, 
from my systems and installed Firefox using the .tar.gz archive which I have extracted simply into ~/Downloads  as I'm the sole user on the machine. If there were other users I would have extracted it into /opt as we're supposed to do.

It all works just the same as it used to when it was a .deb installed version and notifies me when a new version is available to download. 

I occasionally use chromium from a ppa, never the snap, and apart from my Android tablet where it used to be my browser, I've never used Chrome, and even on Android now I never use Chrome, having switched to Brave.

I'm using the bog standard Firefox, almost certainly a snap, but it seems fine to me. I'm not a fan of snap browsers TBH, but they seem to be trying with Fx. Can you recommend a good (Ubuntu/Debian) alternative non-Chromium browser? I would like a back-up.

---

### Post by Daveski17 on 2023-05-30
Looks like the fix patch has worked. At least for Chrome. Brave is still toast.

---

### Post by Daveski17 on 2023-05-31
Brave is back (after an update). Hurrah!

---

### Post by Daveski17 on 2023-05-31
Firefox is definitely reverting back and staying as my default after this fandango.

[IMG]https://i.imgur.com/QLs9ZOU.png[/IMG]

---

