---
title: "Defining java variables"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by core on 2006-02-28
Hi
I've installed java sdk manually with the .bin from sun.com, but i'm having a problem: i dunno how to make ubuntu understand that it's sun's jvm i want to be used.
I know of a way of officialy install java in ubuntu but I was with some repositories problems at the time so i downloades the bin and tried to install it myself.

update-alternatives --config java doesn't list Sun's JDK. How can I put it n the list?

I've edited my ~/.bash_profile, adding this:

JAVA_HOME=/usr/local/bin/j2sdk1.4.2_10/
PATH="${JAVA_HOME}"/bin:"${PATH}"

but i have to do

. ~/bash_profile

to load it every time I logon. Also i'd like it to by system wide, i mean, not restricted to the terminal context.

I hope i explained my self correctly. Thanks in advance.

---

