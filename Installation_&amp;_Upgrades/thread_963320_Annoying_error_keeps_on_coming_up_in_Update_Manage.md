---
title: "Annoying error keeps on coming up in Update Manager and any Synaptic!"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by fikelfikel on 2008-10-30
This error, when checking for new programs or updates keeps on coming up:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Please look at the screen shot below. I'm using an Huwai E220 on Hardy, and actually, could you please have a look at my error that I'm having upgrading to 8.10? [http://ubuntuforums.org/showthread.php?t=963291](http://ubuntuforums.org/showthread.php?t=963291)

Please help!

---

### Post by Partyboi2 on 2008-10-30
Try changing your download server in Software Sources.

---

### Post by fikelfikel on 2008-10-30
> **Partyboi2 said:**
> Try changing your download server in Software Sources.

Nope, just made the checking slower from the main server than the Irish one. This error came up and think it's the same one:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Partyboi2 on 2008-10-30
Open a terminal and try
```
sudo apt-get update -o Acquire::http::No-Cache=true

```

---

### Post by fikelfikel on 2008-10-30
> **Partyboi2 said:**
> Open a terminal and try
```
sudo apt-get update -o Acquire::http::No-Cache=true

```

Actualy, I clicked the "more" in the server selection in Software Sources. It said the best one for me was "Switzerland" and was faster than ever. It works perfectly with the Distro Upgrade wizard, which didn't work before. I'll try your other command in the Terminal later. Thanks

---

