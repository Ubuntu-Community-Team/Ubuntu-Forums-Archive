---
title: "ubuntu10.10 apt-get GPG key lost."
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by melon1234 on 2010-10-15
My system is ubuntu10.10 x64. After a system wide crash, the apt-get does *not* work now for all repository servers. What is this problem related to? How can I regain the needed GPG key? Does all ubuntu update mirror site use same GPG public key? Thank you in advance.

--
ShenLei

=======
run:
# sudo apt-get update
get:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mörgæs on 2010-10-15
[http://www.ubuntuforums.org/showthread.php?t=1590829](http://www.ubuntuforums.org/showthread.php?t=1590829)

---

