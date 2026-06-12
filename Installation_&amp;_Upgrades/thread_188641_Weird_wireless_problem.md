---
title: "Weird wireless problem"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by ipaidforthisname on 2006-06-04
Hello,

I just upgraded from Breezy Badger to Dapper Drake, and love it, but I've had a few odd issues that I haven't been able to solve on my own. One of the most perplexing is my wireless problem. My wireless card was detected during the installation, and I just had to extract the firmware from the .sys using the fwcutter program. 

The wireless card works fine now, but everytime I boot, it doesn't work until I do these three things:

```
 
$sudo ifconfig eth1 down
$sudo ifconfig eth1 up
$sudo /etc/init.d/networking restart

```

After that, it works without a hitch until I reboot again, and I have to keep doing that. 

Does anyone have any ideas as to how I can avoid doing that each boot?

Thanks!

Edit: I know this is posted in the wrong forum now. Is there any way to delete it?

---

