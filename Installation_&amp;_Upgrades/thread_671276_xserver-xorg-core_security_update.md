---
title: "xserver-xorg-core security update"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by MarkCrossley on 2008-01-18
When I try to download the latest security update I get the following message

```

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb
  403 Forbidden

```

Any suggestions?

---

### Post by PmDematagoda on 2008-01-18
The update is defective as it causes Java applications to malfunction. The update is currently being worked on and a fix should be released soon after which you can download and install the update.

---

### Post by Michael_Grosberg on 2008-01-18
I get the same problem.

---

### Post by rabbito on 2008-01-18
same here, good to know there is a good reason why it will not update though.

---

### Post by wog on 2008-01-18
> **PmDematagoda said:**
> The update is defective as it causes Java applications to malfunction. The update is currently being worked on and a fix should be released soon after which you can download and install the update.

If the current update causes Java applications to fail, why does the system still signal this upgrade? What ungodly mess does it fix that makes updating to it better than staying with whatever one already has installed? :D

---

### Post by p_quarles on 2008-01-18
There were five security fixes in the update, four dealing with possible privilege escalation. They're working on the 403 issue, and I believe that's resolved now.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

---

### Post by ward83 on 2008-01-18
It worked for me now, I was getting the 403 error all morning. Note that if you're using the update manager, you have to click 'Check' to get the new repository info. This is the equivalent of doing 'apt-get update' from the command line.

---

### Post by rexless on 2008-01-18
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)

I still cannot get this file to download.

---

### Post by oscarsfriend on 2008-01-18
That's because it is the broken package which has been blocked!  You want the fixed update: [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.2_i386.deb)

---

### Post by rexless on 2008-01-18
ok, that's great, but how do I tell Update Manager to look elsewhere?  Shouldn't the update manager know this already?

---

### Post by oscarsfriend on 2008-01-18
I had to run adept (the package manager I use), then tell it to fetch updates, before the update manager would see the updated packages.  You should also be able to install the update from the command line with apt-get, I suppose.

---

### Post by rexless on 2008-01-18
Sweet... ok.  click "Check" then it downloads the latest list of updates, then click "Update" and away it goes.  Thx.

---

### Post by ubername on 2008-01-18
Ward83 's answer worked for me.

"It worked for me now, I was getting the 403 error all morning. Note that if you're using the update manager, you have to click 'Check' to get the new repository info. This is the equivalent of doing 'apt-get update' from the command line."

Thanks Ward83

---

### Post by erfahren on 2008-01-18
how funny - I just got this error too - then came to here to the forums and this was the very first thread in the list of new posts!

"sudo apt-get update" worked for me as well

---

### Post by bazmati on 2008-01-19
hi, i clicked onthe link in oscarfriends post,  the install failed with a red warning that it conflicts with another package .. at that point i clicked synaptic update again and this time it was able to update my system and the update icon on my task bar went away.  
:guitar:

---

