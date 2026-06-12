---
title: "update problem"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by tiosus on 2010-09-17
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ir.archive.ubuntu.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ir.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by flick on 2010-09-17
This happens at times during archive updates. My first advice would be to wait a bit -- half hour say -- and then try your update and upgrade again. This has happened to me every once in a while, a little patience always paid off.

---

### Post by tiosus on 2010-09-17
i changed update server and solved!!!!!1

---

