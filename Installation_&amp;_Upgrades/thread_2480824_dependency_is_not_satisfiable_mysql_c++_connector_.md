---
title: "dependency is not satisfiable mysql c++ connector install gdebi"
date: 2022-11-11
forum: Installation &amp; Upgrades
---

### Post by nick-mirthmaker on 2022-11-11
been fighting with this for a while. I'm trying to install the mysql c++ connector on my ubuntu install.
In short:

I go here:
[https://dev.mysql.com/downloads/connector/cpp/](https://dev.mysql.com/downloads/connector/cpp/)
go to the ubuntu - 22.04 version (the version I'm running right now)
libmysqlcppconn9_8.0.31-1ubuntu22.04_amd64.deb worked just fine, but thats not the one I want, I believe the one I want is:
libmysqlcppconn-dev_8.0.31-1ubuntu22.04_amd64.deb

but when I do that
(using sudo gdebi ./libmysqlcppconn-dev_8.0.31-1ubuntu22.04_amd64.deb )

I get an error "This package is uninstallable, Dependency is not satisfiable: libmysqlcppconn8-2 (= 8.0.31-1ubuntu22.04)

any thoughts?

---

### Post by &amp;KyT$0P# on 2022-11-11
I haven't used GDebi in years, but I don't think it can do this type of installation.  Looks like you would need to download **all** the .deb packages that site offers for your Ubuntu version, then install them all at once in a single [FONT=Courier New]apt[/FONT] command.

For example, if you have a folder containing nothing other than the deb packages downloaded from that site, you could open a Terminal in that folder and run
```
sudo apt install ./*.deb
```

---

### Post by nick-mirthmaker on 2022-11-11
Thank you for the suggestion. Unfortunately I got this error:

[IMG]https://i.ibb.co/fXYTBQd/Dev-help-install.png[/IMG]

There were 2 files that started off the same as libmysqlcppconn8-2... so I re-downloaded both of them, and got the same error.

any thoughts?

---

### Post by &amp;KyT$0P# on 2022-11-11
That package is downloadable from the same site from [here]("https://dev.mysql.com/downloads/mysql/").  But that download page has a link to [this]("https://dev.mysql.com/downloads/repo/apt/") which, if it's what I think it is (I didn't download it to check), looks like it'd be much easier than trying to install this stuff from manual downloads.

---

### Post by nick-mirthmaker on 2022-11-16
didn't seem to work,

tried some other things.
bricked my computer
re-installed ubuntu to get it working again.
gave up for a bit.

I think I found the solution though, super simple, I can just "sudo apt-get install libmysqlclient-dev " and that gives me the 'mysql.h' header i needed apparently.

for some reason I was lead to believe I needed a jdbc.h file (other tutorials used that) but apparently the mysql.h header is what I needed.

(but knowing me, I'll come to realize that I do indeed need the jbdc file later, but for now, I'm hopeful that I do not)

---

