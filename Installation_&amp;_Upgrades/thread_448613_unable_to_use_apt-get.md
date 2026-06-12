---
title: "unable to use apt-get"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by lub0 on 2007-05-19
Hi All,  I have done a search on this subject in the forums,  but i dont see anything specific on my problem. Here go's, 

I am using 6.06 and have recently started using ubuntu, I am trying to install java. Firstly through apt get, then synaptic and i understand that synaptic uses apt get for updates anyway.

Neither gave me what i was looking for as limewire still would not work  :(

I also installed automatix to see if i could resolve the problem, it uses apt get aswell  :(

now when i try to install/update using apt get i get this error:

sudo apt-get update

Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing freeciv-data (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_etch_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I googled this problem before posting and seen a thread saying to add:
Acquire::http::Proxy "false";
APT::Cache-Limit "8388608";  to the /etc/apt/apt.conf, This made no difference either

Any help would be greatly appreciated..  :)

thanks.  

lub0

---

### Post by taurus on 2007-05-19
Can you post your /etc/apt/source.list?

```
cat /etc/apt/sources.list
```

---

