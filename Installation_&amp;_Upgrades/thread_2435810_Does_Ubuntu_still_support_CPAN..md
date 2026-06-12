---
title: "Does Ubuntu still support CPAN."
date: 2020-01-26
forum: Installation &amp; Upgrades
---

### Post by chown clown on 2020-01-26
Does Ubuntu still support CPAN.  I can open it but cannot download install modules in either 16 or 14.  thanks in advance for our help

---

### Post by guiverc on 2020-01-26
All 14.04 LTS release are EOL, with only Ubuntu 14.04 ESM still being supported by Ubuntu Advantage provided by Canonical.

Lubuntu 16.04 LTS was a flavor of Ubuntu, flavors of Ubuntu come with only 3 years of support (excluding Ubuntu-Kylin 16.04 LTS which had 5 years for that release only).

When releases go EOL, some resources are erased, mirrors disappear etc.

Ubuntu also uses the *year.month* (yy.mm) for major desktop/server releases; yes a few specialist releases do use *year* only, such as Ubuntu Core 16 which is intended for IoT appliances.

---

### Post by TheFu on 2020-01-26
cpan has moved to **cpanm**. If cpan.org is even still up, that's a surprise.  The perl community moved to cpanm about 8 yrs ago.

Also, if you are loading modules from cpanm (or formerly cpan), then perhaps using **perlbrew** is something you need?  Having a self-contained, non-OS connected perl and perl module installation is considered a best practice by all scripting language communities.  With perlbrew, we can have 15 different perl versions, each separate from the others AND from the OS perl.  When Canonical needs to change something about perl or perl modules as part of the OS, our perl programs/webapps aren't impacted at all.  For many, the main reason they use perlbrew is to have a current perl version on their systems. 

Perlbrew is like **rbenv**, **pyenv**, if you know those for the other languages.  Every program you create can have a different perl, if you like.  It is a very powerful concept, implemented in a simple, Unix, elegant, way through control of environment variables.

Perlbrew will change your life. Seriously.  cpanm works perfectly inside that environment, as expected.  Want to refresh all current metacpan modules for a specific perl version?  Switch to the perl version using perlbrew, then a simple:
```
cpan-outdated | cpanm
```
all modules are updated.

---

### Post by chown clown on 2020-01-31
Thank you, i will look into this.  I was able to get CPAN to work and upload the modules.  BUT my cgi scipts dont work in the browser and only come up as code.  Thanks for your help.  I have not had to set up a server in a while

---

### Post by chown clown on 2020-01-31
Thank you for that info.  With cpanm, do you know if the MCPAN -eshell works the way it should?    I was able to install my modules with it.   But the cgi scripts do not work. They open in my browser as code.   Maybe the old eshell does not work anymore?   it has been 8 years since i installed a server.   I guess a lot has changed.

---

### Post by chown clown on 2020-02-01
thank you for your help

---

### Post by Skaperen on 2020-02-01
CGI scripts coming up as code sounds like a server issue.

---

### Post by chown clown on 2020-02-02
It is an apache issue.  I have installed apache2.4, and seems works differently than 2.2.   I configured everything correctly. But the offensive line in my httpd.conf is "[COLOR=#000000][FONT=&quot]LoadModule cgid_mode modules/mod_cgid.so"  i used perlbrew to load my CGI modules. I think i got that one correct.  Not too sure where to find this mystery module.   Thanks for your help.[/FONT][/COLOR]

---

