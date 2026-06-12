---
title: "Unable to upgrade Ubuntu. &quot;Failed to start omid.service: Unit omid.service not found&quot;"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by gavannon on 2018-10-09
I'm using Ubuntu 16.04.5 LTS xenial, server.

After doing apt-get update without issue, apt-get upgrade returns the following:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]

```

I say **yes**, and get the errors:

```

Setting up scx (1.6.3.659) ...
Failed to start omid.service: Unit omid.service not found.
dpkg: error processing package scx (--configure):
 subprocess installed post-installation script returned error exit status 5
Errors were encountered while processing:
 scx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried apt-get clean which returns no errors. And apt-get install -f and dpkg --configure -a return the exact same errors above. How is this error resolved?

---

### Post by gavannon on 2018-11-02
Anyone?

---

### Post by aryanace0001 on 2018-11-03
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code
I get stuck at this step everytime please.

---

### Post by gavannon on 2018-11-03
I appreciate the sarcasm.

Originally this post had the specific error message as the title: "Failed to start omid.service: Unit omid.service not found."

That got zero responses for over a week, so I renamed the title of this post to be more click-baity. Apparently no one has ever heard of omid.service.

---

### Post by Holger_Gehrke on 2018-11-04
You at least managed to get me to look at your post ... A short search for 'scx omi Linux' showed me pages about 'Microsoft System Center' server management software and its Unix client agent named scx which relies on omiserver (OMI=Open Management Infrastructure). So if your server is part of a network in which this is used, than that's where you should look for the solution.

Holger

---

### Post by gavannon on 2018-11-05
Thanks Holger_Gehrke.

You may be onto something with it being Microsoft related. I've recently switched to Azure, and in my years I've learned one key thing: if you're using multiple products, and one of them is by Microsoft, and something goes wrong ... it's probably the Microsoft product.

I'll see what I can learn and update here if I succeed.

---

### Post by ggoulet on 2019-01-02
Have you had any luck gavannon? I'm having the same issue ... ;-/

---

### Post by oldos2er on 2019-01-02
Please create your own thread, gavannon hasn't been back to the forum for a couple months.

---

