---
title: "apt-get pass configure options"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by arthurccube on 2010-01-22
Hi Guys,

I am using apt-get install for nginx.

I need to pass the options "./configure --add-module=/path/to/my/push_module" as if I am going to build from source.

Is it possible?

Thanks a bunch
Arthur

---

### Post by diesch on 2010-01-22
To which program you need to pass this options?

---

### Post by arthurccube on 2010-01-22
Nginx!

---

### Post by arthurccube on 2010-01-22
I am using the Comet (Push Server), so I need to add the push server module.

---

### Post by diesch on 2010-01-23
Sorry, I don't understand what you want to do.

apt-get is for installing .deb packages, it can't do anything else.  From your description it seems to me that software you want to install isn't a .deb package but something else, maybe a .tar.gz containing source code.

---

### Post by arthurccube on 2010-01-23
Hi,

Let me clarify it a bit.

I want to install nginx with a module called nginx_http_push_module. The module if install from source is as follows:

([http://pushmodule.slact.net/](http://pushmodule.slact.net/))
./configure --add-module=path/to/nginx_http_push_module


However, I want to use "apt-get install nginx" to install nginx together w/ the module. 

How can I do so?

Thanks!
Arthur

---

### Post by diesch on 2010-01-23
No. You have to install the nginx package using apt-get and then install the module either direkt from source or by first creating a packge from source and then installing that package.

If you want to create a package see [https://wiki.ubuntu.com/PackagingGuide/](https://wiki.ubuntu.com/PackagingGuide/)

---

### Post by arthurccube on 2010-01-23
Hi Diesch,

Thanks for your reply again! I am coping w/ what apt-get doing now.

Normally, e.g. if I install nginx + openssl, I can 
1. apt-get install nginx package
2. apt-get install openssl package

Nevertheless, I don't know if the module package can be install as normal, since:
"Modules are added **by compiling them along with the Nginx source.**"

Can I create a package for the Nginx Push Module **via compiling the pre-installed nginx package**?, i.e.
1. apt-get install nginx
2. apt-get install push_module // [B] compiling them along with the Nginx source.

[/B]I have no experience in making packages, sorry for the stupid questions if it is too obvious.

Arthur

---

