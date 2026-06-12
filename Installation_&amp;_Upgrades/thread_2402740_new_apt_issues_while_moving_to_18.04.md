---
title: "new apt issues while moving to 18.04"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by gobo7 on 2018-10-03
i've been using 14.04 with a local repository.  in preparation for a move to 18.04,
i've set up an 18.04.1 test machine to help find issues.  found some!
apt-get update issues some errors i've not seen before (listed below.)  the main
issue is apt-get is not actually updating.  a simple apt-get install vim returns
no candidate found.

so i've missed a step or two somewhere.  would be grateful for suggestions.
thanks.

my sources.list file for a usb drive:
```

deb [trusted=yes] file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic main restricted 
deb [trusted=yes] file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic universe
deb [trusted=yes] file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic multiverse
deb [trusted=yes] file:///media/user1/reposb/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic-security main restricted universe
deb [trusted=yes] file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse

deb-src [trusted=yes] file:///media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic main restricted universe multiverse

```


here are the errors from apt-get update.
```

N: Download is performed unsandboxed as root as file '/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic/InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch file:/media/user1/reposb/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic-security/main/binary-amd64/Packages  File not found - /media/user1/reposb/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic-security/main/binary-amd64/Packages (2: No such file or directory)
E: Failed to fetch file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-48x48.tar  File not found - /media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-48x48.tar (2: No such file or directory)
E: Failed to fetch file:/media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic-updates/main/dep11/icons-48x48.tar  File not found - /media/user1/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic-updates/main/dep11/icons-48x48.tar (2: No such file or directory)
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

just for completeness, this is my initial mirror.list.
```

############# config ##################
#
set base_path /mnt/reposB/ubuntu1804
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     4
set _tilde 0
#
############# end config ##############

# 64Bit
deb-amd64 http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-amd64 http://security.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu bionic-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse

# 32Bit
deb-i386 http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-i386 http://security.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse


# Source
deb-src http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu bionic-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu bionic-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse

```

again, thanks for the assistance in jumping "a few" releases.

---

