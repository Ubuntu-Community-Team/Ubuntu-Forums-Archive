---
title: "Anybody using 'nginx' web server software?"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cookiecruncher on 2010-01-20
I recently installed 'nginx' webserver on my alpha2 install, but I had a problem displaying css graphics correctly.

I subsequently found they were stored in '/images' under the page root directory.  Looking under the '/var/log/nginx/error.log' I was getting errors like
> "/usr/share/images/img01.jpg" failed (2: No such file or directory)After investigation found an entry in '/etc/nginx/sites-available/default' file with a path
> #location /images {
    #    root   /usr/share;
    #    autoindex on;
    #}which I hashed out.  This seems to have fixed the problem.

Maybe this should be filed with Launchpad?  Not sure what my fix has done to the operation of 'nginx' tho.

---

