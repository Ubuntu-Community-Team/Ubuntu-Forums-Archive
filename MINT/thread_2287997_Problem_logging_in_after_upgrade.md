---
title: "Problem logging in after upgrade"
date: 2015-07-23
forum: MINT
---

### Post by Ali_B on 2015-07-23
Hi,

Hope someone can help here.

I recently did an update on Mint 17.  What I did was as follows...

sudo apt-get update
sudo apt-get upgrade

Everything seemed to go okay, although I had a couple of questions regarding merging /etc/issue and possible 1 or 2 others.  I told it to replace the current versions.

After a reboot, I get my normal GUI login screen, however my login/password does not work.  I tried CTRL-ALT-F1 to log in there, but also fail to login.

Rebooting to recovery mode, logging in as root, mount filesystem as RW, and then using passwd to reset my user password seems to work fine, although when rebooting again and trying the login, it doesn't work.

Any ideas?

Thanks
Alister

---

