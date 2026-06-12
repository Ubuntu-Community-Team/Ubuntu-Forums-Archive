---
title: "Package vs source installation in terms of maintainability (for server)"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by GSMD on 2006-09-06
Hello.
Could you please share your thoughts on the following subject: is it better to install software from packages or from source?
As far as I understand, the software that is installed from packages will b&#1091; automatically updated as new versions are added to the repository, while compiled sofware has to be updated manually.
But what will happen if I try to install e.g. apache from source while a version installed from package already exists?

E.g. if a new critical bug is discovered but the update is not in reposotory yet.

A kind of punning post, sorry ;)

---

### Post by az on 2006-09-06
> **GSMD said:**
> 
But what will happen if I try to install e.g. apache from source while a version installed from package already exists?

E.g. if a new critical bug is discovered but the update is not in reposotory yet.

A kind of punning post, sorry ;)

You can use a tool like equivs to circumvent the package manager dependencies, but it's not a good idea.  The turnover time for uploading security updates into the repos in Ubuntu is the best in the industry, though.

I would say that anything that is in main will get excellent security updates coverage.  Many apps in Universe, too - YMMV.

Due to the long life cycle of Ubuntu Dapper, you may want to run the LAMP stack from main, and then upload you web application to your server from source, and keep the web application up-to-date yourself.  Not a lot of web applications are packaged for Ubuntu anyway.

---

