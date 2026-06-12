---
title: "[Solved] How to burn the Ubuntu iso to usb in Linux?"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by dxxvi on 2013-07-19
I only found posts about burning the Ubuntu iso to a pen drive in an existing Ubuntu environment. Unfortunately, I don't have a Ubuntu machine here, but I have a machine with Arch on it. Does anybody know how do that in Arch?

Thank you.

---

### Post by darkod on 2013-07-19
I'm not sure, but I think it should work if you simply dd it to the pendrive. But MAKE SURE you use the correct device, otherwise you can overwrite one of your hard drives and lose the OS or important data.

The dd command would be like:
```
dd if=/path/isofilename.iso of=/dev/sdXX
```

You might need to do it as root or with sudo rights, not sure how Arch works for this. And make very, very sure you use the correct /dev/sdXX, in other words your pendrive!!! If you put your hdd as destination in the of= option, it will overwrite the first 700MB of it applying the iso over it. So watch out!!!

---

### Post by sudodus on 2013-07-19
> **darkod said:**
> I'm not sure, but I think it should work if you simply dd it to the pendrive. But MAKE SURE you use the correct device, otherwise you can overwrite one of your hard drives and lose the OS or important data.

The dd command would be like:
```
dd if=/path/isofilename.iso of=/dev/sdXX
```

You might need to do it as root or with sudo rights, not sure how Arch works for this. And make very, very sure you use the correct /dev/sdXX, in other words your pendrive!!! If you put your hdd as destination in the of= option, it will overwrite the first 700MB of it applying the iso over it. So watch out!!!
+1
If you want help finding the correct target device id for the dd command, you can use a shell-script from this link[URL="http://ubuntuforums.org/showthread.php?t=1958073"]

Howto make USB boot drives[/URL]

---

