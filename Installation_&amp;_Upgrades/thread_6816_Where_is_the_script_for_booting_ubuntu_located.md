---
title: "Where is the script for booting ubuntu located?"
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by Borgmeister on 2004-12-01
As above, cos i want to see if i can stop ubuntu 'configuring network devices' on boot, and hence speed boot

Thanks guys

---

### Post by diebels on 2004-12-01
[http://www.tldp.org/HOWTO/From-PowerUp-To-Bash-Prompt-HOWTO-6.html](http://www.tldp.org/HOWTO/From-PowerUp-To-Bash-Prompt-HOWTO-6.html)

---

### Post by diebels on 2004-12-01
Try
```
grep 'configuring network' /etc/init.d/*
```
And edit the relevant scripts. I'm at Hoary at the moment where some of these scripts are changed so I can't be more spesific.

---

### Post by adbak on 2004-12-01
Are you talking specifically of "shpchp" and "pciehp"?

If so, here's what I did to skip those FATAL errors:
```
sudo emacs /etc/hotplug/blacklist
```
add "shpchp" and "pciehp" to the bottom of the list, but without the quotation marks and on their own lines.
Save and quit.

That should save some seconds when booting up.

---

### Post by Borgmeister on 2004-12-02
its 'configuring network interfaces...' on boot up. im assuming its merely trying to get an ip for a network. i want to stop this happrning, 

i hope that is a little clearer.

thanks aagaib

---

