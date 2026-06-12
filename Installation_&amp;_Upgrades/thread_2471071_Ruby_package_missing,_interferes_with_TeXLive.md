---
title: "Ruby package missing, interferes with TeXLive"
date: 2022-01-20
forum: Installation &amp; Upgrades
---

### Post by lenveen on 2022-01-20
Today I installed LaTeX on my Lenovo laptop running Ubuntu 20.04.3. It seems that a ruby package was missing and this messed with some of the LaTeX installation:
```

Errors were encountered while processing:
 ruby
 rake
 texlive-lang-japanese
 texlive-full
 context
 context-modules
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby2.7/libruby2.7_2.7.0-5ubuntu1.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby2.7/libruby2.7_2.7.0-5ubuntu1.5_amd64.deb)
     404  Not Found [IP: 2001:67c:1562::18 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby2.7/ruby2.7_2.7.0-5ubuntu1.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby2.7/ruby2.7_2.7.0-5ubuntu1.5_amd64.deb)
     404  Not Found [IP: 2001:67c:1562::18 80]
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ruby:
 ruby depends on ruby2.7; however:
  Package ruby2.7 is not installed.

dpkg: error processing package ruby (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rake:
 rake depends on ruby:any | ruby-interpreter; however:
  Package ruby is not configured yet.
  Package ruby-interpreter is not installed.

dpkg: error processing package rake (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-japanese:
 texlive-lang-japanese depends on ruby; however:
  Package ruby is not configured yet.

dpkg: error processing package texlive-lang-japanese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-full:
 texlive-full depends on texlive-lang-japanese (>= 2019.20200218); however:
  Package texlive-lang-japanese is not configured yet.

dpkg: error processing package texlive-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:
 context depends on ruby | ruby-interpreter; however:
  Package ruby is not configured yet.
  Package ruby-interpreter is not installed.

dpkg: error processing package context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context-modules:
 context-modules depends on context (>= 2018.04); however:
  Package context is not configured yet.

dpkg: error processing package context-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ruby
 rake
 texlive-lang-japanese
 texlive-full
 context
 context-modules

```
The filename omitted in the transcript above is "libruby2.7_2.7.0-5ubuntu1.5_amd64.deb".
I cannot find the missing package by a simple web search, although a package with the "1.5" replaced by "1.6" does exist. Since this is the latest LTS Ubuntu and widely-used software (TeXLive) I find this strange. Can I safely ignore this, or should I manually install the 1.6 package and get it to work aith TeXLive?

---

### Post by Impavidus on 2022-01-21
Version 2.7.0-5ubuntu1.6 is the one in the repositories. 2.7.0-5ubuntu1.5 must be an old version, so your package manager is using outdated information. Try refreshing repository information, then try installing again.```
sudo apt update
```

---

### Post by lenveen on 2022-01-24
Thanks, that seems to have solved the problem. The 1.6 package is now installed and I got no more complaints from TeXLive.

---

