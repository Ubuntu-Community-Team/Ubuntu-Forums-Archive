---
title: "After update+upgrade+dist-upgrade, no ethernet, no wireless and will not shutdown"
date: 2016-04-02
forum: Installation &amp; Upgrades
---

### Post by inalandofplenty on 2016-04-02
Dear all,

Been browsing these forums for years and always found something to help me out without having to post. Until now! There's a first time for everything :D

Issue: after fresh install of 14.04 on a Dell Vostro 1000, ethernet was working but wireless wasn't (so about what you would expect), I did *sudo apt-get update*, then *sudo apt-get upgrade* and then *sudo apt-get dist-upgrade*. Now there is no ethernet, no wireless, and it hangs indefinitely during shutdown. I have never had anything like this happen before and could not find anything similar in other threads.

Do any of you have any suggestions?

Thanks in advance!

---

### Post by kansasnoob on 2016-04-03
That first update would almost certainly have included a kernel update so I'd see if maybe the older kernel still works OK by choosing it from the advanced grub boot menu.

---

### Post by inalandofplenty on 2016-04-04
Thank you! I will try it and let you know.

---

