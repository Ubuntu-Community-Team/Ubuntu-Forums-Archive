---
title: "Software Update Failure messages"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by KWLLC on 2014-01-10
I am using ubuntu 12.04 LTS on a 64-bit Dell Inspiron 1525 (Intel® Pentium(R) Dual CPU T2370 @ 1.73GHz × 2). I have been notified that updates are available but the Update Manager is 
failing. The error messages I get imply that my Internet connection is failing but I have tested it and it is working fine. The messages are:

   Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.15.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.15.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.15.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.15.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_25.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_25.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/t/thunderbird/xul-ext-gdata-provider_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/t/thunderbird/xul-ext-gdata-provider_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/t/thunderbird/xul-ext-lightning_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/t/thunderbird/xul-ext-lightning_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/t/thunderbird/xul-ext-calendar-timezones_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/t/thunderbird/xul-ext-calendar-timezones_24.1.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]  

I have been out of the loop for a while with health issues so I'm stumped. I have never seen so many system failure messages and unexpected program shutdowns as I have seen lately.
And these are basic programs: Software Center, LibreOffice, etc.  Should I upgrade to a different version of the system? I thought LTS would be conservative and stable. 

[SIZE=5]Any[/SIZE] thoughts or opinions are[COLOR=#00ffff] [/COLOR][COLOR=#ff0000]welcome[/COLOR][COLOR=#00ffff].[/COLOR] Thank you for your time.

---

### Post by ian-weisser on 2014-01-10
Refresh your package cache: [B]sudo apt-get update
[/B]
404 doesn't mean you lack connectivity
It means you *have* connectivity, but the desired file simply does not exist.

So let's pick one at random:
[http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.15.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.15.3-0ubuntu0.12.04.1_amd64.deb)
If you open that in a web browser, you do indeed get a 404 error.

Let's find out why:
```
$ rmadison -u ubuntu libnss3 | grep 12.04
 libnss3 | 3.15.3.1-0ubuntu0.12.04.1      | precise-security | amd64, armel, armhf, i386, powerpc
 libnss3 | 3.15.3.1-0ubuntu0.12.04.1      | precise-updates  | amd64, armel, armhf, i386, powerpc
```

Look closely at the version numbers:
.../nss/libnss3_**3.15.3-0ubuntu0.12.04.1**_amd64.deb
**3.15.3[COLOR=#ff0000].1[/COLOR]-0ubuntu0.12.04.1**

You seem to be looking for a package that has incremented. That usually happens if your package cache is old.

---

