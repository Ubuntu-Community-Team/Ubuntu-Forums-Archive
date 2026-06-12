---
title: "[SOLVED] apt-get producing warnings"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by amitst on 2008-06-12
I am getting the following errors every time I am running apt-get (for more than 2-3 weeks now),
```

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz  404 Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I am able to receive and install updates for the other repositories. Is it advised to remove all of the above lines from the sources.lst?

---

### Post by PmDematagoda on 2008-06-12
Are you running Ubuntu Edgy? If so then it has become unsupported and it's repositories have been moved, so you would need to find the location of the edgy repositories archives.

---

### Post by amitst on 2008-06-12
I am running Hardy Heron. I had initially installed Edgy and then upgraded after every six months to come to Hardy. Looks like the entries in the sources.lst haven't vanished. Should I simply delete the lines saying previous version names (other than hardy)?

---

### Post by PmDematagoda on 2008-06-12
> **amitst said:**
> I am running Hardy Heron. I had initially installed Edgy and then upgraded after every six months to come to Hardy. Looks like the entries in the sources.lst haven't vanished. Should I simply delete the lines saying previous version names (other than hardy)?

Yes, you should be able to solve the problem simply by removing the edgy repositories.

---

