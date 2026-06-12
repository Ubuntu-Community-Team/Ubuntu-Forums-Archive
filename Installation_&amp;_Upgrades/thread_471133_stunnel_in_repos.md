---
title: "stunnel in repos?"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by bAdSkAtEr on 2007-06-11
I have seen it mentioned that stunnel is available in the repos, but I cannot seem to find it for 6.06.1 Server/LTS.  "apt-get install stunnel", "apt-get-install install stunnel3", and "apt-get install stunnel4" all fail to find anything for version 6.06.1 Server/LTS:

sudo apt-get install stunnel4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package stunnel4

I have found I can install stunnel this way on my desktop (7.04 Desktop, very recent install).  "stunnel" appears to install stunnel v3, and stunnel4 installs v4.  But, again, no luck on 6.06.1 Server.

Similarly, "aptitude search stunnel" returns to entries (v3 and v4) for 7.04, but nothing for 6.06.1

I am new to Ubuntu and hope I am just missing something...

Thanks,

Joe

---

### Post by christhemonkey on 2007-06-11
On the 6.06.1 server you probably just need to enable the universe repository where stunnel resides.

```
sudo nano /etc/apt/sources.list 
```

And there should be some lines which are commented out (ie beginning with a #) that have the word "universe" (without quotes) in them.
Uncomment these, then save and quit nano (Ctrl+X then Yes)
Then type:
```
sudo apt-get update
sudo apt-get install stunnel4 
```

---

### Post by bAdSkAtEr on 2007-06-11
Thank you for your quick, and accurate, response.  Works like a charm.

Thanks,

Joe

---

