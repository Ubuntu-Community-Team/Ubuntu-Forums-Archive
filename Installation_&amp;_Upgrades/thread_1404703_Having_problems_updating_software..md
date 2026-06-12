---
title: "Having problems updating software."
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by dudemang on 2010-02-11
Hey, was wondering if anyone had any advice.  I'm on 9.10 right now and trying to update all my software (as well as download a few others).

Whenever I run sudo apt-get update, I get the following:

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
  401  Unauthorized [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
  401  Unauthorized [IP: 91.189.88.45 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-)                                                                                                                      i386/Packages.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/bin](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/bin)                                                                                                                      ary-i386/Packages.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/b](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/b)                                                                                                                      inary-i386/Packages.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/b](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/b)                                                                                                                      inary-i386/Packages.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/)                                                                                                                      Sources.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/sou](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/sou)                                                                                                                      rce/Sources.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/s](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/s)                                                                                                                      ource/Sources.gz  401  Unauthorized [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/s](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/s)                                                                                                                      ource/Sources.gz  401  Unauthorized [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used                                                                                                                       instead.


I've tried sudo apt-get install debian-archive-keyring, however, That also did not work.  Any suggestions?

---

### Post by howefield on 2010-02-11
Try changing the server you are downloading from.

System > Administration > Synaptic Package Manager > Ubuntu Software tab > Download from....

---

### Post by dudemang on 2010-02-11
Forgot to mention that I already tried that.  Same issue.

---

### Post by howefield on 2010-02-11
Are you using a proxy ?

---

### Post by dudemang on 2010-02-11
No.

---

### Post by dudemang on 2010-02-11
Ugh...major facepalm.  So I this whole time I've been trying to figure out this problem remotely, and as soon as I got to my computer, I opened up Firefox and figured it out.

I made the assumption I had internet access this whole time (valid IP address and SSH/SFTP into this machine all day long).  Well, when I opened Firefox and it asked me for my login name and password, many expletives began spewing from my mouth.

Thanks for the help anyways :P

---

