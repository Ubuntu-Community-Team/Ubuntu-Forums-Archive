---
title: "Circular dependencies, problems building anjuta"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by Homayoon on 2006-10-11
Hi. I'm running Dapper and recently I've encountered some strange experience building anjuta from source code. Since I do not currently have Internet access I have to download any needed packages from within the side-by-side Windows XP. Since anjuta said to be dependent on XML::Parser perl package I downloaded and tried to install the relevant dependency packages until I came to libhtml-tree-perl (libhtml-tree-perl_3.19.01-1_all.deb) and libwww-perl (libwww-perl_5.803-4_all.deb), each of which says to be dependent on the other to be installed. I'm quite confused. I'm a newbie in Linux and Ubuntu (although I'm quite experienced in computers and programming), but this does not seem to be logical!

By the way, what C++ IDE do you thing is the best to run under Dapper? Is anjuta all right, or you probably suggest something else?

---

### Post by mcduck on 2006-10-11
you can install many deb packages at the same time, like 'sudo dpkg -i package1.deb package2.deb package3.deb'.This way you can install packages that depend on each other :)

---

### Post by Homayoon on 2006-10-11
It worked! I said I am newbie, after all!

P.S.: Now I should install GLib 2.0. It seems I'm going to keep switching between Windows and Ubuntu every 2 minutes! :( This is going to continue until my internet connection gets okay. All hail the ADSL!!!

---

### Post by kuja on 2006-10-11
> **Homayoon said:**
> Hi. I'm running Dapper and recently I've encountered some strange experience building anjuta from source code. Since I do not currently have Internet access I have to download any needed packages from within the side-by-side Windows XP. Since anjuta said to be dependent on XML::Parser perl package I downloaded and tried to install the relevant dependency packages until I came to libhtml-tree-perl (libhtml-tree-perl_3.19.01-1_all.deb) and libwww-perl (libwww-perl_5.803-4_all.deb), each of which says to be dependent on the other to be installed. I'm quite confused. I'm a newbie in Linux and Ubuntu (although I'm quite experienced in computers and programming), but this does not seem to be logical!

By the way, what C++ IDE do you thing is the best to run under Dapper? Is anjuta all right, or you probably suggest something else?

I find KDevelop to be a rather nice C++/multilanguage IDE.

---

