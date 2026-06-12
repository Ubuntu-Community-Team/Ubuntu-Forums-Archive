---
title: "Update manager fails"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Azegul on 2008-06-28
The update information is outdated. This may be caused by network problems. Please update manually by clicking on this icon and then selecting 'Check'

This is the message I get from Update manager. If I use sudo apt-get update
I get these messages: 

W: Failed to fetch [http://ubuntu.ipacct.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://ubuntu.ipacct.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  404 No such domain

W: Failed to fetch [http://ubuntu.ipacct.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://ubuntu.ipacct.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  404 No such domain

E: Some index files failed to download, they have been ignored, or old ones used instead.

Etc, etc...

I've tried changing the server to main and to best available, but no change. I've changed my sources list to the original and others I have found in other posts. The internet works fine for other programs. But I can't install programs from synaptic or Add/Remove programs. Here is the message I get :

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Any suggestions?

Thanks :)

---

### Post by AlexBellisBrown on 2008-06-28
Which version of Ubuntu are you using? Hardy?

---

### Post by Azegul on 2008-06-28
My apologies. Hardy with Gnome

---

### Post by Azegul on 2008-06-28
Wow! Feel stupid. With more searching this is what fixed it for me:-

opening up Synaptic Package Manager (System>Admin>Synaptic Package Manager and click on Settings>Preferences>Network.

I had synaptic set up for my proxy at home! Duoh....

Thanks :)

---

### Post by Azegul on 2008-06-28
Too quick off the mark!

That DIDN'T fix it......

Too much coffeeeeee

---

### Post by Azegul on 2008-06-28
Restarted the computer and it's working now.
Network proxy had been set for my home network....
:?

---

### Post by AlexBellisBrown on 2008-06-28
Very good! :D

---

### Post by Azegul on 2008-06-28
These forums are why I use Linux. :)

---

### Post by AlexBellisBrown on 2008-06-28
Yup, I heard it said the other day, why pay microsoft for "support" if all you get is some fat *** lady paid $7 an hour to run you through a troubleshooting guide she probably doesnt understand?? This forum is the best place for Linux support, or any OS come to think of that, alot of the users here helped write code for programs too, so you actually talk to people who "built" Linux. I doubt fat *** lady did that!! :):):)

---

