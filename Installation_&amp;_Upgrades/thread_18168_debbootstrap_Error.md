---
title: "debbootstrap Error"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by abhaysahai on 2005-03-05
Hi,
I am trying to install Ubuntu from Gentoo linux. 
Going as per the instructions at [http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html)
I downaloaded debbootstrap and tried to install Ubuntu.
At First the bootstrapper could not download the Release file so I manually downloaded it and coppied it to 
/mnt/ubuntu/var/lib/apt/lists/debootstrap.invalid_dists_hoary_Release
Then I ran the bootstrapper again 
bash -x /usr/sbin/debootstrap --arch i386 hoary /mnt/ubuntu [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

( I have tried with "bash -x /usr/sbin/debootstrap --arch i386 warty http://archive.ubuntu.com/ubuntu" too with the same effect :-# )

It downloads packages.gz and tries to download all the required packages, However the URL from which it downloads is "http://archive.ubuntu.com/ubuntu dists/hoary/main/binary-i386/Packages"
Which I could not foind. 
I have tried multiple versions of debbootstrap file and various mirrors, but could not download a single Package. 
Below is the errornous output 

 for p in '"$@"'
+ for c in '$COMPONENTS'
+ local details=
+ for m in '$MIRRORS'
+ local path=dists/hoary/main/binary-i386/Packages
++ apt_dest pkg hoary main i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dists/hoary/main/binary-i386/Packages
++ case "$1" in
++ local m=http://archive.ubuntu.com/ubuntu
++ m=debootstrap.invalid
++ printf %s var/lib/apt/lists/
++ echo debootstrap.invalid_dists/hoary/main/binary-i386/Packages
++ sed 's/\//_/g'
+ local pkgdest=/mnt/ubuntu/var/lib/apt/lists/debootstrap.invalid_dists_hoary_main_binary-i386_Packages
+ '[' '!' -e /mnt/ubuntu/var/lib/apt/lists/debootstrap.invalid_dists_hoary_main_binary-i386_Packages ']'
+ continue
+ '[' '' '!=' '' ']'
+ progress 0 0 DOWNDEBS 'Downloading packages'
+ local now=0
+ local end=0
+ local name=DOWNDEBS
+ local 'fmt=Downloading packages'
+ shift
+ shift
+ shift
+ shift
+ '[' '' ']'
+ '[' '' ']'
+ '[' '' '!=' done ']'
+ error 1 COULDNTDL 'Couldn'\''t download %s' adduser
+ local err=1
+ local name=COULDNTDL
+ local 'fmt=Couldn'\''t download %s'
+ shift
+ shift
+ shift
+ '[' '' ']'
+ '[' '' ']'
+ '[' yes ']'
++ LANG=
++ gettext debootstrap 'Couldn'\''t download %s'
+ printf 'E: Couldn'\''t download %s\n' adduser
E: Couldn't download adduser
+ exit 1
+ exit_function
+ local n=0
+ '[' 0 -lt 0 ']'
+ N_EXIT_THINGS=0


Please tell me what am i doing wrong.
Is there some basedebs.tar file which help in downloading all the base packages ( like we have in debian). I dont want to download the install iso.

Regards,
Abhay :confused:

---

