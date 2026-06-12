---
title: "Help need to install tar.gz software"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by vkr0704 on 2010-06-22
Hello I am installing one software (pwDesktop [[http://home.pw/desktop/]](http://home.pw/desktop/]))

I am following these stapes
$tar -xzvf pwDesktop-release.tar.gz
then
$./configure
but it saying there is nosuch file or directory

---

### Post by sf-it-services on 2010-06-22
you may need to make....... try more ./README

---

### Post by sf-it-services on 2010-06-22
make ./configure
make ./install

blah blah

---

### Post by atomizer on 2010-06-22
I think you forgot to cd into the directory where the configure-script is.

probably ```
tar -xzvf pwDesktop-release.tar.gz
cd pwDesktop-release
./configure
```

---

### Post by vkr0704 on 2010-06-22
> **sf-it-services said:**
> you may need to make....... try more ./README

Hi
there is no ./README file

---

### Post by vkr0704 on 2010-06-22
> **atomizer said:**
> I think you forgot to cd into the directory where the configure-script is.

probably ```
tar -xzvf pwDesktop-release.tar.gz
cd pwDesktop-release
./configure
```


ya i do this but there is no such file or directory

---

### Post by vkr0704 on 2010-06-22
> **sf-it-services said:**
> make ./configure
make ./install

blah blah

result of $make ./configure

make: *** No rule to make target 'configure'. Stop.

same for $make ./install

pls help

---

### Post by sf-it-services on 2010-06-22
what are you trying to install, and what flavour linux do you have

---

### Post by vkr0704 on 2010-06-22
> **sf-it-services said:**
> what are you trying to install, and what flavour linux do you have

ubuntu 10.04

---

### Post by oldos2er on 2010-06-22
This is a ready-to-run executable, no compiling necessary. Double-click the **pwDesktop** file.

---

### Post by vkr0704 on 2010-06-23
> **oldos2er said:**
> This is a ready-to-run executable, no compiling necessary. Double-click the **pwDesktop** file.

I run this command $sudo ./pwDesktop
but i got this error

" ./pwDesktop: symbol lookup error: 
/usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_malloc_n "

---

### Post by oldos2er on 2010-06-23
I think you're more likely to get help here: [http://feedback.home.pw/forums/43953-pw-web-feedback](http://feedback.home.pw/forums/43953-pw-web-feedback)

---

