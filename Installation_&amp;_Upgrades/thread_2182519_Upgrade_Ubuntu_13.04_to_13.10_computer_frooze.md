---
title: "Upgrade Ubuntu 13.04 to 13.10 computer frooze"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by Arrowman2 on 2013-10-21
Hello,

My computer frooze during the upgrade proces from Ubuntu 13.04 to 13.10. It did not respond for more than two hours, so I shut it down by pushing the power button for 5 seconds. Now it starts with Ubuntu 13.10, but parts of the interface are missing. For example all the options at the right top of the screen are gone, so I can not shut of the computer normally. Also I can not reach the terminal trough the interface. I can use the internet.

I am not very experienced with Ubuntu.

Thanks for any tips or help how to solve this.

---

### Post by heir4c on 2013-10-21
For terminal use Ctrl+Alt+t
and type:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

