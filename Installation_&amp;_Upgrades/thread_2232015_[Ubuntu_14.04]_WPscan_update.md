---
title: "[Ubuntu 14.04] WPscan update"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by phobos2 on 2014-06-29
Hi everyone , so I'm facing a really anoying problem :s
I've followed all the instructions to install wpscan on ubuntu 14.04 :

```
sudo apt-get install libcurl4-gnutls-dev libxml2 libxml2-dev libxslt1-dev ruby-dev


```
```
git clone https://github.com/wpscanteam/wpscan.git


```
```
cd wpscan


```
```
sudo gem install bundler && bundle install --without test development

```

Wpscan works perfectly , but when I try :
```
ruby wpscan.rb --update


```

It gives me this error :
```
__          _______   _____                  
        \ \        / /  __ \ / ____|                 
         \ \  /\  / /| |__) | (___   ___  __ _ _ __  
          \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \ 
           \  /\  /  | |     ____) | (__| (_| | | | |
            \/  \/   |_|    |_____/ \___|\__,_|_| |_|

        WordPress Security Scanner by the WPScan Team 
                        Version v2.4.1
     Sponsored by the RandomStorm Open Source Initiative
   @_WPScan_, @ethicalhack3r, @erwan_lr, pvdl, @_FireFart_
_______________________________________________________________

[i] Svn / Git not installed, or wpscan has not been installed with one of them.
[!] Update aborted
```

So anybody have an idea to fix the problem ? Thanks =)

---

### Post by claracc on 2014-07-06
Is git software package installed in your system?

You can see it in synaptic, if not installed, install it.

---

### Post by phobos2 on 2014-07-06
Yep git is already installed

---

### Post by phobos2 on 2014-07-07
Bump

---

