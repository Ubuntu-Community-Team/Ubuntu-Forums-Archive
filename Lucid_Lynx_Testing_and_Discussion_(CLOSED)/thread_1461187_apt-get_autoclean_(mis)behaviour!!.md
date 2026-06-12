---
title: "apt-get autoclean (mis)behaviour!!"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BugBuster on 2010-04-23
Over a period of time I have used the above command to delete packages in the cache that can no longer be downloaded. Thats what it is meant to do as per the apt-get man page.

But over the last few distros..since 9.04 probably..I have noticed that it does not work the same.

In Synaptic I have selected the option to keep all the downloaded packages. However when I run this command , apt-get -s autoclean, it tries to remove packages that were just installed, say after an update.

Also over a period of time several of the installed packages that are still installed suddenly disappear from the cache. I need to keep this installed packages for as long as I don't delete them myself.

Please help.

---

### Post by wilee-nilee on 2010-04-23
You definitely don't want to run autoclean or autoremove after a kernel update before you reboot. sudo apt-get autoremove and sudo apt-get autoclean is how I would use this. I just use the cleaner in Ubuntu tweak it will short, of bleachbit or computer janitor remove more cache and configs then either of the cli commands. Not sure why it is removing what you want to save, but it is two different programs, I don't think apt-get is set to read a saved package in synaptic, just a theory.

---

### Post by mmalone21 on 2010-04-23
I had the same issue and ended up using computer janitor. It seemed to do the job.

---

### Post by Rubicon_82 on 2010-04-23
> **BugBuster said:**
> However when I run this command , apt-get -s autoclean, it tries to remove packages that were just installed, say after an update.

What is the status of the package that apt is trying to autoremove?  This can be checked with the command:
```

apt-cache policy <package_name>

```
Apt sometimes fails to correctly update the package descriptions 'apt-get update' is run.  I've often observed that running an update shortly after the 'Packages.bz2' files are updated on the Ubuntu servers results in an error such as:
```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

As a result of this, apt will temporarily think that the relevant packages can no longer be downloaded, and are therefore valid candidates for autocleaning.  The problem will usually resolve itself after a few hours.  With a development release, this type of error is common, as the package descriptions are updated frequently.

> 
Also over a period of time several of the installed packages that are still installed suddenly disappear from the cache. I need to keep this installed packages for as long as I don't delete them myself.


There is a cron job for apt that undertakes housekeeping activities for the package archives.  You should look at the '/etc/cron.daily/apt' script.  It is fairly well documented with regards to apt.conf options that can be used to alter its behaviour.

---

### Post by BugBuster on 2010-04-24
> What is the status of the package that apt is trying to autoremove?

Sorry..my bad. I did not mean to say the packages are removed as in un-installed but deleted from the package cache. Please read the entire thread with regards to the packages stored in the cache.Nothing to do with installing/uninstalling them.

Also I came across this:

> The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

in the apt-get man page. 
But where do I set it to off?

---

### Post by mc4man on 2010-04-24
> But where do I set it to off?
Most likely in /etc/apt/apt.conf (may not exist so create

```
gksu gedit /etc/apt/apt.conf
```

```
APT::Clean-Installed "off";
```

---

