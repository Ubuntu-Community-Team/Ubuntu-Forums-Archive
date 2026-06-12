---
title: "Problems with apt-get"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by Folley on 2012-01-26
Folks,

I'm trying to verify and install some programs in Ubuntu (64bits, version 11.10, oneiric), but I'm receiving the following error:

=====================================
Get:97 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) oneiric-backports/universe Translation-en [5,524 B]                                                                       
99% [90 Translation-en bzip2 0 B] [62 Packages bzip2 277 kB]                                                                                       365 kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) oneiric/universe i386 Packages                                                                                               
  404  Not Found
99% [87 Translation-en gzip 400 kB] [Waiting for headers]                                                                                          365 kB/s 0sE: Unable to parse package file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en.decomp (1)
Fetched 22.9 MB in 1min 5s (349 kB/s)                                                                                                                         
W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://br.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en  

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
=====================================

Someone know if there are any problems with the packages? Because sounds like the packages are corrupted.

Regards,

---

### Post by cortman on 2012-01-26
Whoa! What command were you running to install? Are you trying to install from a repository or a downloaded tarball or deb?

Looks like you edited your sources.list, and that's throwing everything off. Is that right? If you're installing from a local package, you don't have to touch that file.

Answer some of my questions above, and we'll see if we can get it sorted out!

---

