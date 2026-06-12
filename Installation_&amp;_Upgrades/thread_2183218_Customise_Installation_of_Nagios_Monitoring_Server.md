---
title: "Customise Installation of Nagios Monitoring Server"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by devraj2 on 2013-10-24
Hello,

I am new to Linux. I want to install Nagios Monitoring server on customised location Linux. I was successful in installation and configuration but **it automatically install in /usr/local/nagios**. But **I want to install it in /etc/ or in /opt/nagios**

For this kind of installation where and how do i make changes to setup this successfuly.

Please help me to resolve this issue.

---

### Post by ian-weisser on 2013-10-24
If you use the package manager, you must move the files manually after installation. The package manager does not give you a choice (for good reasons). This method is not recommended, as you may be unable to uninstall the package (file not found), and any upgrades will reinstall to the original location.

To define custom application paths, you must either build your own .deb package, or install manually.

Generally, /etc is not an expected location for applications.
In Ubuntu, /opt is generally reserved for non-repository applications to prevent namespace collisions. For example, a manually-installed version of nagios.

---

