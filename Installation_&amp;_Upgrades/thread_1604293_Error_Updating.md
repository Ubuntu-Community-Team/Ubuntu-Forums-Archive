---
title: "Error Updating"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Airforcefalco on 2010-10-23
I'm trying to update the ubuntu on my laptop but it gives me this error and I'm not sure how to fix it (aside from the old windows fix, delete and reinstall)

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


I installed ubuntu while I was in windows so it looks like a file that I could just delete (i dont know the term for that type of installation). I am on a 64-bit system.

If you need anything else let me know.

---

### Post by Airforcefalco on 2010-10-24
/bump

P.S. Why do you guys have a link to digg and not reddit? Digg committed suicide when it released v4.

---

### Post by tommcd on 2010-10-24
> **Airforcefalco said:**
> 
I installed ubuntu while I was in windows so it looks like a file that I could just delete ...

So does this mean that you installed Ubuntu inside Windows using **wubi**? If this is the case, then you should know that Wubi was only meant for people to try out Ubuntu. It was never meant to be used to upgrade to the next version of Ubuntu:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle. 
So if you have been using Ubuntu for a while inside Windows with Wubi, then it is time that you did a real install to a dedicated linux partition on your hard drive.
So did you install Ubuntu using Wubi? Or did I not understand you correctly and this is a real linux install you are talking about? Please write back for further assistance.

---

