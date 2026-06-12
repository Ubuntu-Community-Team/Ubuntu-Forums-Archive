---
title: "Ruby 1.9 installation"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by anero on 2010-02-05
Hi guys,

I've been trying to install ruby 1.9.1 using both aptitude and apt-get on karmic but I haven't been able to make it work.
First I tried removing the previous installed version (1.8.7) and then installed package *ruby1.9.1-full* using aptitude, which was supposedly correctly installed but then running *ruby* command from the shell does not work.
Then I removed all ruby-related packages using aptitude and tried reinstalling using *apt-get install ruby* but this package installs version 1.8.7 :(

Have anyone been able to install 1.9.1 version's package (I'm trying to avoid installing from source).

Thanks!

---

### Post by vvlist on 2010-02-05
you've probably installed it correctly, you just have to use it by typing "ruby1.9.1" instead of "ruby". I came here to find out how to rename that path back to just "ruby". Hope that helps.

---

### Post by ratcheer on 2010-02-05
Just create a symbolic link in /usr/bin. Name the link "ruby" and make the target the full path and filename of ruby1.9.1. You will probably want to do a similar thing for irb.

Tim

---

### Post by ratcheer on 2010-02-05
Wait. I'm not sure the above is correct. I use Ruby 1.9 and my system finds "ruby" at /usr/local/ruby-1.9.1/bin/ruby

I do not recall renaming it from anything else, but I installed it several months ago, so I'm not sure.

Tim

---

