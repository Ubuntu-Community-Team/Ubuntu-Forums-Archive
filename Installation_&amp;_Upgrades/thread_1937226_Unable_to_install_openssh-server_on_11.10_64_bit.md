---
title: "Unable to install openssh-server on 11.10 64 bit"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by Snorkr on 2012-03-07
# This is what happens. Any clues?
```

root@snorri-iMac:/opt# apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwrap0:i386 libsamplerate0:i386 m4 libjack-jackd2-0:i386 libnspr4-0d:i386 libjson0:i386 libspeexdsp1:i386 pax
  libasound2:i386 libflac8:i386 libvorbisenc2:i386 rpm librpmbuild2 libasyncns0:i386 libpulse0:i386 librpmsign0
  libvorbis0a:i386 lsb-core alien ncurses-term libnss3-1d:i386 libsndfile1:i386 libasound2-plugins:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra monkeysphere
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0 B/334 kB of archives.
After this operation, 885 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 273325 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.8p1-7ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.8p1-7ubuntu1) ...
Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the home directory of the
                                new account
  -c, --comment COMMENT         GECOS field of the new account
  -d, --home-dir HOME_DIR       home directory of the new account
  -D, --defaults                print or change default useradd configuration
  -e, --expiredate EXPIRE_DATE  expiration date of the new account
  -f, --inactive INACTIVE       password inactivity period of the new account
  -g, --gid GROUP               name or ID of the primary group of the new
                                account
  -G, --groups GROUPS           list of supplementary groups of the new
                                account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           use this alternative skeleton directory
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -l, --no-log-init             do not add the user to the lastlog and
                                faillog databases
  -m, --create-home             create the user's home directory
  -M, --no-create-home          do not create the user's home directory
  -N, --no-user-group           do not create a group with the same name as
                                the user
  -o, --non-unique              allow to create users with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       encrypted password of the new account
  -r, --system                  create a system account
  -s, --shell SHELL             login shell of the new account
  -u, --uid UID                 user ID of the new account
  -U, --user-group              create a group with the same name as the user
  -Z, --selinux-user SEUSER     use a specific SEUSER for the SELinux user mapping

dpkg: error processing openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

