---
title: "The update information is outdated (notification icon)"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by gavinflud on 2012-11-09
Hi all, I'm new to Ubuntu and still trying to get to grips with it so apologies if I've posted this in the wrong area.

I am running Ubuntu 12.10 on a Samsung NP350V5C laptop. I have started getting this icon in the notification bar over the last day or so, even though Software Center is running updates properly and I have no new updates available.

I have followed some tips online and ran ```
sudo apt-get update && sudo apt-get upgrade
``` which seemed to solve the problem. However, it has come back since and doing that again hasn't fixed it.

The output after running "sudo apt-get update" is as follows:

```
W: Failed to fetch http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by arpanaut on 2012-11-09
[http://askubuntu.com/questions/210102/why-skype-doesnt-work-in-quantal](http://askubuntu.com/questions/210102/why-skype-doesnt-work-in-quantal)

apparently that ppa is no longer active use the suggestions on linked page to get skype working from the correct repository.

---

### Post by gavinflud on 2012-11-09
> **arpanaut said:**
> [http://askubuntu.com/questions/210102/why-skype-doesnt-work-in-quantal](http://askubuntu.com/questions/210102/why-skype-doesnt-work-in-quantal)

apparently that ppa is no longer active use the suggestions on linked page to get skype working from the correct repository.
Thanks for that. Just had to delete some .list files created by Software Center. All back to normal again.

---

