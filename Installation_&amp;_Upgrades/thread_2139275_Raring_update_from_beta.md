---
title: "Raring update from beta"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by jsmeche on 2013-04-26
Hello,

I have been running 13.04 beta for a while and whenever I run an update, the last few lines of the update process look like this
```

Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com raring Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Can anyone please tell me what a GPG error is, why it is not desirable and how I can go about fixing it. Thanks

---

### Post by slickymaster on 2013-04-26
GPG errors are related to missing Launchpad GPG keys for all the PPAs you have added to your software sources. If you want to know about GPG keys, please see this: [The GNU Privacy Handbook]("http://www.gnupg.org/gph/en/manual.html")

To fix it, run these commands at a terminal window:
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

