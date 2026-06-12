---
title: "Can I upgrade to Dapper from a mounted ISO file?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by roncrump on 2006-06-04
Hi,

I was wondering if I could mount the alternative Dapper CD ISO file and upgrade from Breezy from there?

I do not have a CD burner on this computer, but thought downloading the torrent of the CD might be a safer option than running the upgrade tool in case my network connection goes down. Which it is quite likely to do given the amount of up time required for the upgrade.

Ron.

---

### Post by llamakc on 2006-06-04
In the past I've used file-based repositories, so I don't see why you could not mount the iso with loop and add it as the only line for sources.list as:

deb file://path/to/mounted/

run apt-get update and dist-upgrade.

I'm curious if this will work.

---

### Post by llamakc on 2006-06-04
I guess that would have to be:

deb file://path/to/mounted/iso/ dapper main contrib universe multiverse

---

