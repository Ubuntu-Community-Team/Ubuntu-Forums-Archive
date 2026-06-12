---
title: "flickernet"
date: 2008-12-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2008-12-18
on my last update I got the following error:
> * Installing 1 assembly from libflickrnet2.1.5-cil into Mono
! Assembly /usr/share/cli-common/policies.d/libflickrnet2.1.5-cil/policy.2.1.FlickrNet.dll does not exist
dpkg: error processing libflickrnet2.1.5-cil (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libflickrnet2.1.5-cil

I ran ```
sudo dpkg -a --configure
```
and
```
sudo apt-get install -f
```
neither one worked, is this significant?

---

### Post by directhex on 2008-12-18
It's a lesson in why running a development release too early is ill-advised.

The bug has been tracked down, a workaround to libflickrnet will be published soon.

---

### Post by theozzlives on 2008-12-18
How soon is to soon for a print server (not really a server just the one my printer's connected to)???

---

### Post by DougieFresh4U on 2008-12-18
Just checked for updates and there where 7 (U.S. archive) and 'libflckrnet' seem to be resolved as updated went through and no errors. :p

---

### Post by directhex on 2008-12-18
> **theozzlives said:**
> How soon is to soon for a print server (not really a server just the one my printer's connected to)???

Given your "server" is running a development pre-release... any time before April would be an entirely appropriate level of "soon"

However, since the breakage broke CD building, and Alpha 2 is due imminently, a workaround package was rushed through.

```
libflickrnet (25277-6ubuntu2) jaunty; urgency=low

  * Add mono-1.0-devel to build-dependencies as a workaround for a
    mis-build due to al and sn not being provided correctly by
    mono-devel; this should be dropped again once mono is fixed.

 -- Steve Langasek <email address hidden>   Thu, 18 Dec 2008 18:17:32 +0000
```

---

