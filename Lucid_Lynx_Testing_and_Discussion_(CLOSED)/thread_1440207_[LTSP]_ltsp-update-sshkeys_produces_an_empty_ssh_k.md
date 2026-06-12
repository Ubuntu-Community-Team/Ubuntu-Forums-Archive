---
title: "[LTSP] ltsp-update-sshkeys produces an empty ssh_known_hosts file"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nick_stokie on 2010-03-27
Hi,

I've running Ubuntu Lucid (up to date as of 25 Mar 10) with ltsp-server 5.2.1-0-ubuntu4 and ltspfs 0.6-0ubuntu1

LTSP previously worked okay under an earlier version of Lucid (about Alpha 1). I've just built a new ltsp image using ltsp-build-client which completed with no errors. However /opt/ltsp/i386/etc/ssh/ssh_known_hosts is empty (0 bytes) and ltsp-update-sshkeys does not report any errors but produces a fresh empty ssh_known_hosts file. Therefore clients boot to login screen but after entering username and password get "cannot connect to server restarting" message and fail to log in. I'm running ssh is on a non-standard port (2222) but this is unchanged from previous working ltsp versions.

Has anyone experienced a similar problem and/or got any ideas what might be going wrong or the solution?

Thanks,
Nick.

(Apologies if this should be in 'Server Platforms' with other LTSP discussions, I wasn't sure where the best place to post was.)

---

