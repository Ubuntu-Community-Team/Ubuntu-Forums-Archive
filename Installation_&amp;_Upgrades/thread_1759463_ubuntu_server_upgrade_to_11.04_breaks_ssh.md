---
title: "ubuntu server upgrade to 11.04 breaks ssh"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by lilmike2 on 2011-05-15
Hi,
I recently upgraded my server to ubuntu 11.04. IF I remember correctly, I accidentally said keep my current version of some /etc/security/something.conf. Now whenever I try to login with ssh, I get successfully authenticated, then immediately kicked off. I looked in the logs, and it says pam_open_session(): Module is unknown. i think this may have something to do with my security conf file not being upgraded to the package maintainer's version, but not sure. Any help is appreciated.
Thanks,
-Michael.

---

### Post by MAFoElffen on 2011-05-15
> **lilmike2 said:**
> Hi,
I recently upgraded my server to ubuntu 11.04. IF I remember correctly, I accidentally said keep my current version of some /etc/security/something.conf. Now whenever I try to login with ssh, I get successfully authenticated, then immediately kicked off. I looked in the logs, and it says pam_open_session(): Module is unknown. i think this may have something to do with my security conf file not being upgraded to the package maintainer's version, but not sure. Any help is appreciated.
Thanks,
-Michael.
This has went unanswered so I thought I'd say hello and throw out a few ideas...

I remember that when I upgraded one of my servers from 10.10 to 11.04 that it changed the ssh public/private keys.  I had to delete the ~/.ssh folder on my ssh client to renew them on the next login.

If it is the conf files of ssh or something that didn't get updated in that update/upgrade process, you know that you could go to aptitude and reinstall shh -- and you'ld have another chance to review the conf differences and make those decisions again right?

---

### Post by lilmike2 on 2011-05-16
Hi,
That's exactly the problem though. Unless I'm mistaken, I don't think it's something with ssh, it's something in /etc/security/something,conf, which I didn't think was ssh, but I could be wrong. IF anything, it seems to be something with pam, which i don't see how i could reinstall.
Thanks,
-Michael.
Edit: Just reinstalled sshd, no fix.

---

### Post by lilmike2 on 2011-05-17
Hi,
Anyone have any ideas? I am having trouble using my server without sftp to transfer files while my only option is my hosts' out of band access.
Thanks.

---

### Post by lilmike2 on 2011-05-24
Hi,
I'm still really confused, and my server is still broken with ssh. Can anyone please help? I've looked all over the place, but no luck. Perhaps I thought I could reinstall pam, but i don't know how to do this, and googling returned few results.
Thanks,
-Michael.

---

