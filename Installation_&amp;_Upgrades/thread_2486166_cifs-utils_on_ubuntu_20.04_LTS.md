---
title: "cifs-utils on ubuntu 20.04 LTS"
date: 2023-04-21
forum: Installation &amp; Upgrades
---

### Post by jkeels on 2023-04-21
To start with let me explain that I have searched the forums for this information and I may have missed something.  Before I ask a question let me give a little background:
1.  There is a 20.04 workstation used by a client that needs to access an SMB/CIFS share on a server
2.  This was a vendor provided machine
3.  CFIS utils needs to be installed in order to mount an SMB share from the server (workstation does not have internet access so I have to download package and then install it locally on the workstation)
4.  The client is using Ubuntu 20.04 LTS
5.  Due to security concerns our organization is often required to use the LATEST version of a package available for a given purpose.  They want cifs-utils_7.0-2_amd64.deb due to security policy.

Now, I know that cifs-utils_6.9-1ubuntu0.2_amd64.deb will work with ubuntu 20.04 LTS.  However, I am trying to figure out if cifs-utils_7.0-2_amd64.deb will also work properly with Ubuntu 20.04 LTS.
Can this be done or will only CIFS utils 6.9 work with 20.04?

Thanks.  I repeat again that I may be missing a documentation (which I searched for) or a forum post (which I searched for) that already answers this question but I sure didn't find the answer searching the forums, documentation, or using Google.

Thanks.  Oh, its OK to tell me where to find the answer IF the answer to the question is there.  But please, do not be rude, and tell me to RTFM.

Have a nice day.

---

### Post by TheFu on 2023-04-22
It comes down to dependencies.  With large software packages, there could be 50 other dependent packages which aren't moved forward.

If it were me, I'd create an LVM snapshot then install the package version you want and see what dependencies it broke and what other parts to the system were broken.  It would certainly be an unsupported config, which sorta defeats the purpose for using any LTS.  

BTW, you might want to point out to management that security issues ARE corrected by backporting any that are fixed to older LTS versions.  That's sorta the point of running an LTS - we get security fixes AND functionality doesn't change for the release period for 99% of the packages.  [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) has more details.

There are a few packages that get updated with new features. Those tend to be end-user GUI programs like browsers and fat email clients, but on a server, those wouldn't be installed.

In short, for a server, "newer" isn't "better."  I think is can be solved through education of management.

---

