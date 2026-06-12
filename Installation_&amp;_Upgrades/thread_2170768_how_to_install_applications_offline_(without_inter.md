---
title: "how to install applications offline (without internet) on 12.04"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by sai91 on 2013-08-27
Any applications are available which can be installed without the need of internet connection. If so how ? :(

---

### Post by Mark Phelps on 2013-08-27
Basically -- no.  You have to get the applications from somewhere -- that's where the Internet comes in.

You can download apps to one machine and transfer them to another -- but that's a lot of work because of dependencies.  When you download an app on your machine, it looks to see if you have all the dependent packages, and if not, downloads those as well.

If you download the app on another machine, when you go to install it on your, only THEN will it look for dependencies, and if any are missing, you would have to write down the package names, go back to the other machine, and download them there.

---

### Post by ian-weisser on 2013-08-27
The apt-zip and apt-offline packages make offline installation easy. See [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

Caveat:
You need to understand basic package management to understand the offline process: What a dependency is, and why it's bad to mix debs from different releases of Ubuntu.
 You should learn how to use the apt-get and dpkg commands to install and uninstall packages, and how to use apt-cache to search for packages and dependencies.

Using package management offline requires just a couple extra steps (like sneakernetting debs and repository data from the online machine to the offline machine), and it's a supported method of installing software.

It's *really* tempting to simply download non-Ubuntu applications and .debs found in the wild to avoid researching dependencies - DON'T DO IT. Those are not supported, and risk breaking your system. Take a minute, research the dependencies properly, and download *only* from packages.ubuntu.com or other signed and trusted Ubuntu repositories.

---

