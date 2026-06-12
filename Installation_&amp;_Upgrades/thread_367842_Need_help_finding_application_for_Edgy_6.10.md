---
title: "Need help finding application for Edgy 6.10"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by prrawls on 2007-02-22
I'm looking for a version of collectd for Edgy 6.10.

I know the repositories for feisty have this package I just can't find a repository for edgy with this package.  I could build it from source but I would perfer to use a package for the distro. 

This is my first attempt to run a unbuntu server without having to build what I need.  I'm trying to keep this build as clean as possible.  

Any help would be very appreciated. Or maybe a alternative to collectd?  Thank you all!  :)

---

### Post by louis_nichols on 2007-02-22
You could alway sbuild it from the feisty sources. This wouldn't affect your setup...

Just an idea.

---

### Post by prrawls on 2007-02-22
sounds intriguing but whats sbuild?  Sorry for my ignorance.  :)

---

### Post by ramjet_1953 on 2007-02-23
If you go to the coolectd website, there are Debian packages to download, or you could always "roll your own".

[http://collectd.org/](http://collectd.org/)

Regards,
Roger :cool:

---

### Post by louis_nichols on 2007-02-23
> **prrawls said:**
> sounds intriguing but whats sbuild?  Sorry for my ignorance.  :)

Oh. Sorry! That is "always build" instead of what came out. Just a typo. basically, what you need to do is this:
[LIST=1]
[*]add the feisty src repos to your sources.conf
[*]run an ```
apt-get update 
```to refresh the repos
[*]use the command ```
apt-get build-dep *packagename*
``` to download and install dependencies
[*]use ```
apt-get -b source *packagename*
``` to download and build the package. This will install the package without breaking your deb system. The package will then appear in synaptic as installed.
[/LIST]

---

### Post by prrawls on 2007-03-03
Sorry for the long time to reply, thank you very much for everyones help!

---

