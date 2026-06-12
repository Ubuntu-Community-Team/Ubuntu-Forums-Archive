---
title: "Google Chrome stable won't Install- Dependency Error"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by Tinevisce on 2012-07-08
Hello again

I tried installing Google Chrome stable on my Ubunbtu 12.04 (wubi installed, in case that makes any difference); and it kept failing because of a dependency error.

I tried using one of the solutions presented on another website for this very problem, but it didn't really work out.

The solution I followed was this one:
[http://blog.manishchhabra.com/2012/05/installing-google-chrome-in-ubuntu-fix-error-for-missing-package-libcurl3-libnss3-1d-libxss1/](http://blog.manishchhabra.com/2012/05/installing-google-chrome-in-ubuntu-fix-error-for-missing-package-libcurl3-libnss3-1d-libxss1/)


[URL="http://blog.manishchhabra.com/2012/05/installing-google-chrome-in-ubuntu-fix-error-for-missing-package-libcurl3-libnss3-1d-libxss1/"]
[/URL]

---

### Post by scottpledger on 2012-07-08
I had this issue, too. Since I couldn't figure out what the issue was, I just installed FireFox. After using that for about 10 minutes I missed Chrome, so I thought I'd try to figure it out, but when I went to install it, there was no error, so whatever the dependency is, installing Firefox seems to get things going.

TLDR; Try installing Firefox first.

---

### Post by westie457 on 2012-07-08
Hello, have you tried to install those packages independently with ```
sudo apt-get install <package name>
``` for each error, and then trying ```
sudo apt-get install --reinstall <the google chrome package>
```

have not tried this as I use Chromium Browser from the repositories.

---

