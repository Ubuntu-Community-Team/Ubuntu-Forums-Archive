---
title: "Message aftyer running upgrade on Kubunt 12.04 PPC (dual boot on g5)"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by gusduenas on 2013-03-07
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

Hello I have this strange messages after making a fresh Kubuntu 12.04 installation on mac ppc.
After booting for the very first time I've run on the console sudo apt-get update and then sudo apt-get upgrade and it installs a lot of things (not an expert as you could see) then when I run the update I have this messages, now I cannot install git....someone please help is this bad or not? and if not, how could I get rid of.

Thanks,


Gus



W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mörgæs on 2013-03-07
The mirror is not accessible at the moment when you tried. 
Does it work if you wait some hours or switch mirror?

---

