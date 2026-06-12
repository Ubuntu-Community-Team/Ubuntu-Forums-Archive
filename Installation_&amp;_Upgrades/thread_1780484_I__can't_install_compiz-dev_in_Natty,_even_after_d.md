---
title: "I  can't install compiz-dev in Natty, even after downgrading to compiz-0.8.6, please"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by nmvictor on 2011-06-12
I try to i ```
sudo apt-get install compiz-dev 
``` at the terminal and I get the following error:

```

sudo apt-get install compiz-dev 
[sudo] password for nmvictor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-dev : Depends: libgl1-mesa-dev but it is not going to be installed or
                       libgl-dev
E: Broken packages

```
 I don't know what I can do, someone please help. Thanks all.

---

### Post by dino99 on 2011-06-12
several things to check:
- which distro/release is it ?
- is your /etc/sources.list using other links (maybe conflicts)

can try: remove/purge all installed related compiz packages, then reinstall

---

### Post by nmvictor on 2011-06-12
I am using Natty, I did dist-upgrade from Maverick so I suspect that I might be having conflicting compiz sources in my /etc/apt/sources.list. But how do I confirm this and whats the workaround? Thanks fro your reply!

---

