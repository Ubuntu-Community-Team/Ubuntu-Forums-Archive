---
title: "Plone on Dapper"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by hellmet on 2006-11-21
I just installed plone using synaptic...and then ran
 
 /etc/init.d/zope2.8 start

it says no instances found..

localhost:8080/manage 
doesn't work..


Me missing something??
Please letme know.. 

Was easily able to setup on windows...but I shudn't be
talking of the Next -Next thingy anyway..

thanks

---

### Post by ingo on 2006-11-22
read the readme file in the initial directory into which you unpacked the tar.gz file. to start plone:

/opt/Plone-2.5/zeocluster/bin/startcluster.sh

---

### Post by hellmet on 2006-11-24
in installed thru synaptic
also ur command din work

---

### Post by benteveo on 2007-02-07
Here's what you need to do to get plone up and running under edgy:

[LIST]
[*] Install the package 'plone-site' via synaptic
       This brings in many prerequisite packages, mostly of the underlying zope (if you don't have them yet)


[*] When asked add an admin user/password and configure the Zope/Plone admin port.
    The default port is 8081 but whatever you chose is fine.  You may always do this after the install by editing the config file:

    ```
$ sudo *your-favorite-editor* /etc/zope2.9/plone-site/zope.conf
```

    You may want to restart zope, just to be sure it works.
            Either from its own UI:
                ```
 [http://localhost:8081/manage](http://localhost:8081/manage)
```
        or from the shell:
                ```
$ sudo /etc/init.d/zope2.9 restart
```
        (YMMV on the exact version of zope)


[*] Create a plone instance under Zope:
            In the drop-down at the top right next to the Add button, select 'Plone site'
            and click Add.

            The id you give it will be the URL to the instance,
            so if you give it the name mysite, you can access it through:

               ```
 [http://localhost:8081/mysite](http://localhost:8081/mysite).
```


[*] Go to the plone instance you just created and work from there:
            ```
[http://localhost:8081/mysite](http://localhost:8081/mysite)
```

[/LIST]

Enjoy.  Want to do more? There's a ton of documentation in [plone.org]("http://plone.org")

---

### Post by hellmet on 2007-02-08
Ohh.. thanks bentevo..that worked

---

