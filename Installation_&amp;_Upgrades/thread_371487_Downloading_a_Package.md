---
title: "Downloading a Package"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by Synergy55555 on 2007-02-27
Hello All,

   I just downloaded Ubuntu, and I love it already. I'm interested in geting a particular software package ([http://packages.ubuntulinux.org/feisty/science/mpb)](http://packages.ubuntulinux.org/feisty/science/mpb)), however I have no clue how to start. I have version 6.06.1 LTS.  Any help would be appreciated.

Cheers,

Synergy

---

### Post by musings on 2007-02-27
Hi Synergy,

The short answer is to access Synaptic, enable the Universe repositories, then select and install the mpb package.

One minor point: Since you're using Ubuntu 6.06, the standard packages available to you are the Dapper Drake versions rather than Feisty Fawn ones. Here's the link to the mpb package for Dapper: [http://packages.ubuntulinux.org/dapper/science/mpb](http://packages.ubuntulinux.org/dapper/science/mpb)

Regards, Gary

---

### Post by aysiu on 2007-02-27
If you prefer point-and-click, I'd advise [enabling extra repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) and then [using Synaptic Package Manager](http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic) to install *mpb*.

If you are okay with the command-line/terminal and want a quick and simple explanation on software installation, read [this](http://www.psychocats.net/ubuntu/installingsoftware).

**Step 1**: Enable extra repositories (different from the way linked to earlier)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Install *mpb* by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) ```
sudo apt-get update && sudo apt-get install mpb
```

---

