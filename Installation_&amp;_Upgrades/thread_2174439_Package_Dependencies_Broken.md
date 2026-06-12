---
title: "Package Dependencies Broken?"
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by blake4 on 2013-09-14
Hi,

I'm not able to install VLC Media Player, or even update my computer. I get

*This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.*

Then I click More Details and get


The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.8-0ubuntu0.13.04.1) but 2.0.8-0ubuntu0.13.04.1 is to be installed
     Depends: libavcodec-extra-53 (>= 6:0.8.6) but it is not going to be installed
     Depends: libavutil-extra-51 (>= 6:0.8.6) but it is not going to be installed
     Depends: libc6 (>= 2.15) but 2.17-0ubuntu5 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.11-0ubuntu1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.3-1ubuntu1 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.4+dfsg-0ubuntu9.3 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.4+dfsg-0ubuntu9.3 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libstdc++6 (>= 4.6) but 4.7.3-1ubuntu1 is to be installed
     Depends: libtar0 but it is not going to be installed
     Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.9) but it is not going to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.7.dfsg-13ubuntu2 is to be installed

How can I fix this? Thanks.

When I update the system using Terminal, I get

Fetched 817 kB in 29s (27.7 kB/s)
N: Ignoring file 'duinsoft.listsudo' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: GPG error: [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-09-14
For starters, your 404 error.  There is no 13.04 package, you need to remove them and do another update.

[http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/)

---

### Post by blake4 on 2013-09-14
How do I do that? With just a link, I don't undertstand what to do. Also, what do you mean there is no 13.04 package? How do I remove the package?

---

### Post by ibjsb4 on 2013-09-14
You can remove the PPA using your 'software sources'.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

---

