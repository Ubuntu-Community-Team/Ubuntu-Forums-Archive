---
title: "Upgraded to precise, oneiric packages still installed"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by deadtom on 2012-12-22
I upgraded to precise a few days ago using 'do-release-upgrade' from the command line.

I was prompted this morning to upgrade some software and I let it run. It promptly uninstalled chrome, gimp, pidgin and a dozen other bits of software, all relying on libgtk2.0-0.

It turns out that libgtk2.0-0 is still the oneiric version. I checked my sources.list and all my ppas. I found some entries that were still pointing to oneiric sources. I changed those entries to precise and ran apt-get update. Then I removed libgtk2.0-0. I was hoping that I would then be able to run 'apt-get install libgtk2.0-0' and got this error:

```
E: Package 'libgtk2.0-0' has no installation candidate
```

However, according to [http://packages.ubuntu.com/precise/libgtk2.0-0]("http://packages.ubuntu.com/precise/libgtk2.0-0"), there is a current version of libgtk2.0-0 for precise.

For whatever reason, my computer does not know that there is a precise version of libgtk2.0-0. 

There has to be a reference to oneiric still existing somewhere on my system but I can't find it. 

Any ideas?

---

### Post by snowpine on 2012-12-22
The following terminal command will give you info about the version(s) available in your software sources:

```
apt-cache policy libgtk2.0-0
```

---

### Post by deadtom on 2012-12-22
Thanks for responding so fast. I ran that command and this is what it returned:

```
libgtk2.0-0:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.24.10-1oneiric6~ppa 0
        100 /var/lib/dpkg/status
```

It would seem that I have a ppa still pointing to an oneiric source but I can't find it. 'grep oneiric sources.list' and 'grep oneiric sources.list.d/*' return nothing.

---

### Post by snowpine on 2012-12-22
I'm worried you might be missing the Precise "main" repo from your software sources.

```
cat /etc/apt/sources.list
```

Since you are in a state of doubt about your software sources :) you might find this tool useful: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by deadtom on 2012-12-22
> **snowpine said:**
> Since you are in a state of doubt about your software sources :) you might find this tool useful: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


Yup, that was it. Something was missing. I let the site generate a new sources.list for me and everything is installing fine now.

Thank you!

---

