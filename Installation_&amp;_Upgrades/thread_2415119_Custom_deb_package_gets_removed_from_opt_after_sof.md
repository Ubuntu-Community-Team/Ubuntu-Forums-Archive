---
title: "Custom deb package gets removed from opt after software updates"
date: 2019-03-20
forum: Installation &amp; Upgrades
---

### Post by wrootw on 2019-03-20
I have a custom application with a deb installer. I install it either by double clicking and pressing Install in Ubuntu Software window or with sudo dpkg -i package.deb. It installs into /opt/Spark (Spark is the name of the application). I can then use it. But every time i run Software updater and it installs regular system updates, it removes this folder from /opt and i have to reinstall it. Maybe something is wrong with the deb. E.g. VirtualBox Add-ins folder stays in opt (it is a virtual machine).

Ubuntu 18.10
Deb is available here [https://www.igniterealtime.org/downloads/nightly_spark.jsp](https://www.igniterealtime.org/downloads/nightly_spark.jsp)

---

### Post by deadflowr on 2019-03-20
It's probably because Ubuntu's repository has a [spark package]("https://packages.ubuntu.com/cosmic/spark") and it's trying to get installed.
I'd try to run an apt-mark hold on the package to prevent it from being updated.
reinstall the deb and then try
```
sudo apt-mark hold spark
```
See if that stops it from removing the package.

---

### Post by wrootw on 2019-03-21
I will try this command and see if it helps. Although in the long run this is not ideal as i can't instruct every customer to do that.

Btw, i have set subscription for this thread and set it to email immediately and haven't received anything.

Well, after running this command it removes the /opt/Spark folder also.

Hm. After reinstalling and running this command again it wasn't removed this time.

Btw, if i run software update it proposes to install SPARK programming language toolset. I do not select it when installing updates.

---

### Post by again? on 2019-03-21
I would report to igniterealtime.org

---

### Post by wrootw on 2019-03-22
I'm not a developer, but i'm a part of igniterealtime.org community. What should i report or what could be done to deb installer to avoid that?

---

### Post by again? on 2019-03-23
Report that a spark package already exists in debian.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt show spark**
Package: spark
Version: 2012.0.deb-11build1
Priority: optional
Section: universe/devel
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: &#1028;&#1074;&#1075;&#1077;&#1085;&#1110;&#1081; &#1052;&#1077;&#1097;&#1077;&#1088;&#1103;&#1082;&#1086;&#1074; <eugen@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 10.1 MB
Depends: libc6 (>= 2.15), libgcc1 (>= 1:3.0), libgmp10 (>= 2:5.0.1+dfsg-7~), libgnat-6 (>= 6.2.0-5ubuntu12), libstdc++6 (>= 5.2), swi-prolog-vm-3, swi-prolog-nox
Suggests: gnat, alt-ergo
Homepage: http://libre.adacore.com/libre/tools/spark-gpl-edition/
Download-Size: 2,417 kB
APT-Sources: http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
Description: SPARK programming language toolset
 SPARK is a formally-defined computer programming language based on the Ada
 programming language, intended to be secure and to support the development
 of high integrity software used in applications and systems where
 predictable and highly reliable operation is essential either for reasons
 of safety or for business integrity.
 .
 This package contains the tools necessary for checking if programs adhere
 to the SPARK rules and the tools to show freedom of runtime exceptions in
 those programs. To compile SPARK programs use any standards-compliant Ada
 compiler, such as GNAT.
```

Igniterealtime's package will install ok but when you perform system upgrades it will
replace Igniterealtime's spark with the spark language package in the ubuntu repo's
because of the same name but higher build number.

eg I installed Igniterealtime's package then checked upgradable packages.
2012.0 is greater than 2.9.0
```
**[COLOR="#006400"]glen@Bionic:~/Downloads$[/COLOR] apt list --upgradable**
Listing... Done
spark/bionic 2012.0.deb-11build1 all [upgradable from: 2.9.0.SNAPSHOT]
```

I think the only solution is to rename the Igniterealtime spark package to something like spark-ignite.

---

### Post by wrootw on 2019-03-23
So, renaming the app in the installer to something like sparkim should help?

---

### Post by again? on 2019-03-23
Sorry I'm not an expert on building debs....I just know you can't have 2 different packages with identical names.
Whoever is building the debs at igniterealtime should know what to do.

---

