---
title: "URGENT ::: Problem while updating , Ubuntu 9.10"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by anuraggautam on 2010-04-21
Hi,

I am getting problem while upgrading my software repository which cause problems in many other updation of the system.

Error : 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE


Also I have search and applies all possible solution which is available while copying this error to google, but none of solution is working.

Please find screen shot for the same, and let me know the possible solution to get rid from this issue.


Regards,
Anurag

---

### Post by drs305 on 2010-04-21
Does this work?

```

gpg --keyserver keyserver.ubuntu.com --recv-keys EF4186FE247510BE 6B15AB91951DC1E2 && gpg --export --armor EF4186FE247510BE 6B15AB91951DC1E2  | sudo apt-key add - 

```

---

### Post by JOHNNYG713 on 2010-04-21
Try this ! :)
[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/](http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/)

---

### Post by jpaugh64 on 2010-04-21
Is  [http://ppa.launchpad.net]("http://ppa.launchpad.net/") even a valid Ubuntu repository? Forgive me if this is a stupid question.
edit: I couldn't find anything like /ubuntu, /karmic or /pub on that site, though I did see what looked like a repo in one of the subdirectories. If you can expect apt to work for *any* subdir, then that is a new/cool feature for me.

---

### Post by anuraggautam on 2010-04-26
@drs305 : Sorry not able to resolve my problem, here is the result after running command given by you.

gpg: requesting key 247510BE from hkp server keyserver.ubuntu.com
gpg: requesting key 951DC1E2 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

