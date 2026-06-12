---
title: "Installing Sun JDK 5.0"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by vocaro on 2006-09-08
I am working with a clean install of Ubuntu 6.06, and I need to install the official Sun JDK 5.0 (not JRE). I have found several instructions on how to do this, such as:

[serios.net]("http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation#The_different_methods_of_installing_a_JRE.2FJDK")
[intertwingly.net]("http://www.intertwingly.net/blog/2006/05/16/Esse-Quam-Videri")
[ubuntu.com]("https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e-2")

However, none of these instructions works for me. They all talk about a package called sun-java5-jdk, but trying to install this package always gives me a "no package found" error.

I have already edited my sources.list and uncommented the two lines for "multiverse", then did an "apt-get update", but that didn't seem to have any effect.

Is there anything else I can do? Thanks!

---

### Post by greyhill on 2006-09-09
Hey.

That's strange.  It sounds like something's not quite right with your sources.lst file.  Maybe you could post it?

Otherwise, you could start here:
[http://packages.ubuntu.com/dapper/devel/sun-java5-jdk](http://packages.ubuntu.com/dapper/devel/sun-java5-jdk)

and download all the dependencies of sun-java5-jdk individually and install them with "dpkg -i pkgname"

---

### Post by vocaro on 2006-09-09
> **greyhill said:**
> That's strange.  It sounds like something's not quite right with your sources.lst file.  Maybe you could post it?

Sure. The only changes I made were to uncomment the two multiverse lines and, when that didn't work, the universe line as well.

---

### Post by vocaro on 2006-09-09
I figured it out. The instructions I read said "uncomment the multiverse line", or words to that effect. This is wrong. I see now that the only line in sources.list for "multiverse" is for backports. Instead, I needed to add the word "multiverse" to the main line. In other words, this is the line I needed to have in sources.list:

[INDENT]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
[/INDENT]

---

### Post by subnet_rx on 2006-10-23
I'm having the same problems, going to try this, even though I'm not using the .lst file directly, I'm using Adept and thought I unquoted everything but the src repos.

---

