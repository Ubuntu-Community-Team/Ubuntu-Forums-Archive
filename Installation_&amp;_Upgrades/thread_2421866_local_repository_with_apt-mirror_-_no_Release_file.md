---
title: "local repository with apt-mirror - no Release file - can't be authenticated"
date: 2019-06-28
forum: Installation &amp; Upgrades
---

### Post by christian-loeffler on 2019-06-28
Hi all,

i need a local repository for some Ubuntu 16.04 LTS systems.

I used apt-mirror.

my mirror.list

[HTML]############# config ##################
#
 set base_path    /opt/apt-mirror
#
 set mirror_path  $base_path/mirror
 set skel_path    $base_path/skel
 set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0

#
############# end config ##############

deb http://ftp.halifax.rwth-aachen.de/ubuntu xenial main restricted universe multiverse
deb http://ftp.halifax.rwth-aachen.de/ubuntu xenial-security main restricted universe multiverse
deb http://ftp.halifax.rwth-aachen.de/ubuntu xenial-updates main restricted universe multiverse

deb-src http://ftp.halifax.rwth-aachen.de/ubuntu xenial main restricted universe multiverse
deb-src http://ftp.halifax.rwth-aachen.de/ubuntu xenial-security main restricted universe multiverse
deb-src http://ftp.halifax.rwth-aachen.de/ubuntu xenial-updates main restricted universe multiverse


clean http://ftp.halifax.rwth-aachen.de/ubuntu[/HTML]

my sources.list from my local system with the local repository

[HTML]deb http://local_repo/ubuntu/mirror/archive.ubuntu.com/ubuntu/ xenial main restricted
deb http://local_repo/ubuntu/mirror/archive.ubuntu.com/ubuntu/ xenial-updates main restricted[/HTML]

after ***sudo apt update***, i get the following messages 
[HTML]
Holen:1 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial InRelease [247 kB]
Holen:2 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates InRelease [109 kB]
Ign:3 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main amd64 Packages
Ign:4 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main i386 Packages
Ign:5 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main Translation-de
Ign:6 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main Translation-en
Ign:7 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:8 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main DEP-11 64x64 Icons
Ign:9 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted amd64 Packages
Ign:10 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted i386 Packages
Ign:11 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted Translation-de
Ign:12 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted Translation-en
Ign:13 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted amd64 DEP-11 Metadata
Holen:3 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main amd64 Packages [1.201 kB]
Ign:4 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main i386 Packages
Holen:5 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main Translation-de [501 kB]
Holen:6 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main Translation-en [568 kB]
Holen:7 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]
Holen:8 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]
Holen:9 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted amd64 Packages [8.344 B]
Ign:10 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted i386 Packages
Holen:11 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted Translation-de [2.752 B]
Holen:12 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted Translation-en [2.908 B]
Holen:13 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]
Ign:4 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main i386 Packages
Ign:10 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted i386 Packages
Fehl:4 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/main i386 Packages
  404  Not Found
Ign:10 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial/restricted i386 Packages
Ign:14 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main amd64 Packages
Ign:15 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main i386 Packages
Ign:16 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main Translation-en
Ign:17 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:18 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:19 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted amd64 Packages
Ign:20 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted i386 Packages
Ign:21 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted Translation-en
Ign:22 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Holen:14 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main amd64 Packages [986 kB]
Ign:15 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main i386 Packages
Holen:16 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main Translation-en [390 kB]
Ign:17 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Holen:18 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main DEP-11 64x64 Icons [233 kB]
Holen:19 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted amd64 Packages [7.616 B]
Ign:20 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted i386 Packages
Holen:21 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted Translation-en [2.272 B]
Holen:22 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]
Ign:15 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main i386 Packages
Holen:17 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main amd64 DEP-11 Metadata [510 kB]
Ign:20 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted i386 Packages
Fehl:15 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/main i386 Packages
  404  Not Found
Ign:20 http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu xenial-updates/restricted i386 Packages
Es wurden 356 kB in 0 s geholt (944 kB/s).
Paketlisten werden gelesen... Fertig
E: Fehlschlag beim Holen von http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Fehlschlag beim Holen von http://local_repo/ubuntu/mirror/ftp.halifax.rwth-aachen.de/ubuntu/dists/xenial-updates/main/binary-i386/Packages  404  Not Found
E: Einige Indexdateien konnten nicht heruntergeladen werden. Sie wurden ignoriert oder alte an ihrer Stelle benutzt.[/HTML]

Where is my mistake?
What do I have to do to make it work?

---

### Post by Rubi1200 on 2019-06-28
Have you tried changing to another mirror?

Could be they are temporarily down?

Do you get a response with ping?

And welcome to the forums :-)

---

### Post by christian-loeffler on 2019-07-01
Hi,

i tryed several mirrors with no success.

Now i found a solution.
have a look at [https://blog.programster.org/set-up-a-local-ubuntu-mirror-with-apt-mirror](https://blog.programster.org/set-up-a-local-ubuntu-mirror-with-apt-mirror)

BG
CL

---

