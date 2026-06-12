---
title: "[SOLVED] Error updating ubuntu"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by itsols on 2008-11-20
Hi,

I just encountered this error while the automatic update on my Ubuntu 7.10 tried to download and install the latest updates. The errors were:

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://lk.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://lk.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://lk.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


Your inputs are highly appreciated!
Khalid

---

### Post by Nicu Alecu on 2008-11-20
Me 2!
It says:> Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
All 3 packages have "Size mismatch" error.

---

### Post by cdtech on 2008-11-20
Have you tried to change locations and do another "apt-get update"
May even try "sudo apt-get --fix-broken"
Also "sudo apt-get clean"
Then a "sudo apt-get update"

---

### Post by zarqoon on 2008-11-20
Same problem here. Exactly the same packages.
I tried apt-get clean and update. It does not make a difference.
I am still using 7.10 if thats important.

---

### Post by roelpeeters on 2008-11-20
Same problem here... must be something in the repositories

---

### Post by Nicu Alecu on 2008-11-20
> **zarqoon said:**
> I am still using 7.10 if thats important.
Well, I'm on Gutsy too! It seems that it is important, after all ...
And "sudo apt clean" and the others made no difference, indeed!

---

### Post by Devi 710 on 2008-11-20
Same problem here too. I started a thread @ [http://ubuntuforums.org/showthread.php?p=6219963#post6219963](http://ubuntuforums.org/showthread.php?p=6219963#post6219963)

I am running 7.10, I changed the software sources, but I still get the same error.

---

### Post by Partyboi2 on 2008-11-20
Has anyone opened a bug report? I would say there is a problem with the repo.

---

### Post by Devi 710 on 2008-11-20
Sounds like the right thing to do Partyboi2, how would one go about doing that? At the Ubuntu Wiki??

---

### Post by Partyboi2 on 2008-11-20
Over at launchpad. Click on "Report a bug"
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by Nicu Alecu on 2008-11-20
[Other people](http://ubuntuforums.org/showthread.php?t=881596) stumbled upon this kind of error on other occasions. But this one seems to be related to Gutsy and it certainly looks like there's a problem in the repos.

PS: it's already been reported @ [launchpad](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/300418).

---

### Post by itsols on 2008-11-21
Many thanks for your thoughts, all of you. So now I know for sure that it's not a problem with my installation.

Khalid

---

### Post by Nicu Alecu on 2008-11-26
It's been fixed; itsols, you should mark this thread as solved.

---

### Post by itsols on 2008-12-05
Yes, this WAS apparently an error with the repositories. But it's perfectly fine now.

Thanks for everyone's inputs.

---

