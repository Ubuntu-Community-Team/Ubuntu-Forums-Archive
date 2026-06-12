---
title: "Installing OpenNMS w/ Java on 12.04"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by RockinsonM on 2012-08-15
First, my apologies if this belongs in the general help section. I'm running a VM with Ubuntu server 12.04 32 bit. I'm just getting into Ubuntu having very very minor exposure to it in the past. I have been using the OpenNMS tutorial installation document found at [www.opennms.org/wiki/installation:Debian#Select_Your_Release_and_Distribution]("http://www.opennms.org/wiki/installation:Debian#Select_Your_Release_and_Distribution")

While reading through the install document I noticed that during the install of Java that the package isn't available on the latest Debian/Ubuntu releases anymore. The alternative is to either use a private repository or get the binaries and install them manually. 

I opted to get the binary and install it manually.

After installing OpenNMS the tutorial says to configure Java (tell OpenNMS which Java to use) using the "/usr/share/opennms/bin/runjava" command. It then gives an example of the full command (sudo /usr/share/opennms/bin/runjava -S /usr/lib/jvm/java-6-sun/bin/java) however that is for if you installed the recommended Sun/Oracle JDK. I believe this means if you used the package install method which I could not use, although I may be mistaken there. 

Can someone provide me with the proper full command to continue from here? 

For reference, doing an ls of my /usr/lib/jvm directory shows the following child directories:
java-1.6.0-openjdk-i386 (light blue/cyan text)
java-6-openjdk-common (dark blue text)
java-6-openjdk-i386 (dark blue text)
java-7-openjdk-i386 (dark blue text)

Each of those has at least 1 child application file / directory under it, I believe 3 of them have a bunch, java-7-openjdk-i386 just has one that says javaws. If you guys would need me to drill down to a lower level on those to help let me know and I'll list them out.

---

