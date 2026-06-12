---
title: "Ubuntu auto-upgrade, don't know if it worked completely."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by foolios on 2007-11-03
During the upgrade process my system blue - screened and rebooted. I don't know how to check if the ubuntu gutsy gibbon upgrade was successful.

The blue screen was from virtual machine where ubuntu is installed. I am wondering how to know what version of ubuntu is now running.

Where do I find this information? Thanks.

---

### Post by aysiu on 2007-11-03
Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
cat /etc/lsb-release && cat /etc/issue
```

---

### Post by ofb on 2007-11-03
> **foolios said:**
> Where do I find this information?

Well in menu you can do System -> About Ubuntu, and System -> Administration -Update Manager.

The first page of About Ubuntu will include the line "Thank you for your interest in Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007."

And Update Manager will tell you that you can update to 7.10 if you're still running 7.04.

Edit: or you can just do what aysiu slipped in while I was typing..

---

### Post by foolios on 2007-11-09
Thanks for the info, I'll keep it bookmarked.

---

