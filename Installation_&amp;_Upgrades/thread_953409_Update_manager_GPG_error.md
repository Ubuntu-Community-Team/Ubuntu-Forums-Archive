---
title: "Update manager GPG error"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by subseashaun on 2008-10-20
Hi Dudes.

Just tried to update 7.10 using update manager, and had 41 updates to install however prior to it finishing the check it came up with this error message:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

What does this mean and how do I get around it?

Thanks in advance for all replies.

Later

---

### Post by linuxbastard on 2008-10-20
getting this same issue with upgrade manager and #sudo apt-get update on hardy.

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

One other post here says to try to remove the problematic repository, but I don't think that was intended for people having problems with the ubuntu security repository.

---

