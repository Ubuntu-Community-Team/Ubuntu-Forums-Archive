---
title: "Update, software install issues"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Hunnicutt on 2007-06-21
I was hoping someone here could help me out. I have ubuntu on my laptop that I bring from work to home. I love this OS and the ease of use so far. But I have one problem if someone here has an idea of what the issue could be. When I try to update or install software from the Manager I get an error. 

The error for the Manager is (Just pick 3dchess but the error is the same):

W: Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5)
+E-14ubuntu2_i386.deb
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)


W: Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-12_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-12_i386.deb)
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)


and the error for update is:


[http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid
argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:)
Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:)
Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:)
Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:) Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)



Now, when I had this in the office everything was fine, i was able to get many items working this way and do some updates. We do use a Proxy at the office and I thought I removed it from the settings. Is there someplace esle that I need to look? I am a bit of a Linux newby, maybe why I like this Distrobution so much. The other issue is I have a router at home. Other information that might be of use is that I can get on the internet with Firefox and Konquer, as well as my email works fine. 

Thanks for any help and if this is the wrong form for this I am sorry, if someone else had prolbem like it I am also sorry but if you could point it out as I couldn't find it.

Hunni

---

