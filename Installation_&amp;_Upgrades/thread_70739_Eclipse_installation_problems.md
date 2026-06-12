---
title: "Eclipse installation problems"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by jonasforssell on 2005-10-01
Hi,
I have just installed Ubuntu on my laptop.
Trying to install Eclipse with both Add/remove programs and Synapctic gives me error messages. I added universe to the list of servers when Ubuntu asked me but this has not helped. Universe is the only additional server I have.
Here are the errors:
eclipse-jdt:
Depends: eclipse-platform but it is not going to be installed
Depends: junit (>=3.8) but it is not installable
Depends: libant1.6-java (>=1.6.5) but it is not installable
What is the solution? Shouldn't this work out of the box?
Thanks
/Jonas Forssell, Sweden

---

### Post by jonasforssell on 2005-10-02
OK, I think I've found the error.
Enabling Universe as a repository is by default restricted. Going into Synaptic and adding universe again but this time checking all the options before adding will solve the problem.
I recommend installing Eclipse yourself though. The Eclipse dependency is a GNU java implementation which is not 100%. Remove this and install the sun J2SE as a package instead. Finally, download Eclipse from the homepage and do the install yourself. Avoid the Eclipse package.
Other than this, Ubuntu has worked perfectly. It was the only distro being bootable and installable on my Dell C600. Even Gentoo borked!
/Jonas

---

