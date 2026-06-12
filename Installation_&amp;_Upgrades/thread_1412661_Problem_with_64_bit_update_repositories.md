---
title: "Problem with 64 bit update repositories?"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by medphys on 2010-02-21
Hi all,

Has anyone experienced a problem with the64 bit repositories for upgrades?  I have been getting these messages for the last two weeks. 

Failed to fetch [http://mirror.umoss.org/ubuntu/dists/karmic/Release](http://mirror.umoss.org/ubuntu/dists/karmic/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror.umoss.org/ubuntu/dists/karmic-updates/Release](http://mirror.umoss.org/ubuntu/dists/karmic-updates/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://winff.org/ubuntu/dists/Karmic/Koala/binary-amd64/Packages.gz](http://winff.org/ubuntu/dists/Karmic/Koala/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://winff.org/ubuntu/dists/Karmic/universe/binary-amd64/Packages.gz](http://winff.org/ubuntu/dists/Karmic/universe/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have a 64 bit system and tried different sites but I get the same thing with all respositories.

Thanks

---

### Post by manolo on 2010-02-25
Had the same problem.
In Synaptic/Settings/Repositories
In 'Download from' the selection was 'Spain' (Where I live)
I changed to 'Download from' 'Main Server' and now it is Ok.

Hope it helps you :-)

Best regards,
Manolo.

---

