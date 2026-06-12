---
title: "Sun jdk1.6 on lucid 10.04"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rbuick on 2010-02-22
I'm running Springsource Toolsuite and need to use Sun's jdk1.6.

I've installed it in the /usr/lib/jvm directory, alongside the openjdk, created a .jdk1.6.0_18.jinfo file similar to the openjdk .java-6-openjdk.jinfo and run:

sudo update-alternatives --config java

which returns:

There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java 

running:
sudo update-java-alternatives -s jdk1.6.0_18

(even though I had created a .jdk1.6.0_18.jinfo file) returns:

update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
.
.
.
etc.

I note that the man page refers to 'registered jre/jdk...". Is that the key?

To get around my failure above, I set the Sun jdk 6 in a new .bash_profile and removed my .profile in the hope that it would get picked up at login (I've just moved to Ubuntu from Fedora) - it doesn't, and bringing up a Terminal doesn't seem to run .bash_profile either; I have to do:

source .bash_profile

and then I can run Sun's jdk from the Terminal only, elsewhere it still picks up the openjdk.

Any thoughts much appreciated.

Thanks for your time.

---

