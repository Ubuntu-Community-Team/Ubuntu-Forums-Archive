---
title: "Installing php Composer to install Laravel, need openssl enabled"
date: 2022-06-29
forum: Installation &amp; Upgrades
---

### Post by rgbellotti on 2022-06-29
I ran into a roadblock when trying to install Laravel.  I'm using Lubuntu 22.04, and have PHP8.1 installed and working fine.  When I try to install Composer, it says that I first need to "recompile PHP with --with-openssl" option.  Though when I tried to do this, I got an error message that --with-openssl was not recognized as an option.  After researching, the solution I came across was to edit my php.ini, by un-commenting the line where "extension=openssl" and saving it.  So I did this, and now every time I run a PHP script, it runs fine, but it also prints out the warning message: 

"PHP Warning:  PHP Startup: Unable to load dynamic library 'openssl' (tried: /usr/lib/php/20210902/openssl (/usr/lib/php/20210902/openssl: cannot open shared object file: No such file or directory), /usr/lib/php/20210902/openssl.so (/usr/lib/php/20210902/openssl.so: cannot open shared object file: No such file or directory)) in Unknown on line 0"

I don't have a file called "openssl.so" on my hard drive, and haven't been able to find anywhere to download it or find how to write a new version.  The directory in the warning message, / usr / lib / php / 20210902 /  ... does have a lot of .so files in it, so I imagine if I get a copy of openssl.so somehow, I just need to paste it in that directory.

I'd also be open to other ways of installing Laravel, but I do find it concerning that PHP won't utilize ssl without fixing this

---

### Post by rgbellotti on 2022-06-29
I also read that Ubuntu 22.04 started using openssl 3.0.2, instead of 1.1.1, could this create a conflict somehow?

---

### Post by rgbellotti on 2022-06-29
Update:  

Well while I still haven't fixed the missing openssl file problem, Composer still installed because the php.ini file had the option enabled I'm assuming.  So it is still possible to install Composer / Laravel with that missing file warning

---

