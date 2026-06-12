---
title: "Using repositories from Ubuntu Precise"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by miazma on 2012-03-22
Hello,

is it somehow possible to use packages provided by the precise repositories in Oneiric Ocelot (11.10)? I just want to use maven3 from the "official" repository and don't know how the entry must be (deb [http://packages.ubuntu.com/precise/](http://packages.ubuntu.com/precise/) oneiric main) seems not to be right:

sudo apt-get update results in:

W: GPG error: [http://packages.ubuntu.com](http://packages.ubuntu.com) oneiric InRelease: File /var/lib/apt/lists/partial/packages.ubuntu.com_precise_dists_oneiric_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/packages.ubuntu.com_precise_dists_oneiric_main_source_Sources  Encountered a section with no Package: header
...

---

### Post by zvacet on 2012-03-27
Remove that line from your source list and add PPA from [https://launchpad.net/~natecarlson/+archive/maven3 ]("https://launchpad.net/%7Enatecarlson/+archive/maven3")

[]("https://launchpad.net/%7Enatecarlson/+archive/maven3")

---

