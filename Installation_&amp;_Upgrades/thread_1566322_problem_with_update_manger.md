---
title: "problem with update manger"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by RemmyNumber7 on 2010-09-02
I go into update manger and download updates and it tells me

 **Could not download all repository indexes**

then i get this error.  How can I fix this????? 

   	 	 	 	 	 	  GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz)  404  Not Found  
 Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2010-09-03
> **RemmyNumber7 said:**
> I go into update manger and download updates and it tells me

 **Could not download all repository indexes**

then i get this error.  How can I fix this????? 

   	 	 	 	 	 	  GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz)  404  Not Found  
 Some index files failed to download, they have been ignored, or old ones used instead.


For Medibuntu error go [Here](https://help.ubuntu.com/community/Medibuntu) and run the terminal command to install the Medibuntu repository.

For the other error,open **System > Administration > Software Sources** and un-tick the Debian Etch repository.Then Reload the repository indexes.

You should not use the Debian repositories.


Good luck

---

