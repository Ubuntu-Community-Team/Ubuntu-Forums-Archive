---
title: "The disk drive for /tmp is not ready yet or not present"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by JustSteph on 2013-10-10
Hi
I'm running Ubuntu 12.04 and on booting, I get the error message "The disk drive for /tmp is not ready yet or not present. Continue to wait, press S to skip mounting or M for manual recovery" If I wait, it boots after about 20 seconds and everything seems to work fine. I've tried everything I can find from googling this error and nothing has worked, including the fix in the bug report ([https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792)). Can anyone help?
Thanks

---

### Post by heir4c on 2013-10-10
It's a bug:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792)
It wait to mount the /tmp folder, but something disturbs that process.
Sometimes it happen here also but not the /tmp file. Normally I just wait or press S or Enter to go on.

---

