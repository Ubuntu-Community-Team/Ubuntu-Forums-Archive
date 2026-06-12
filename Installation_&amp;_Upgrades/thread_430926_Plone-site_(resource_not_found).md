---
title: "Plone-site (resource not found)"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by ronb on 2007-05-02
I have Zope installed and running, and I get the following at this URL ([http://localhost:8081/manage):]("http://localhost:8081/manage%29:") 

 **Zope Version** (Zope 2.9.6-final, python 2.4.4, linux2)
**Python Version** 2.4.4 (#2, Apr 12 2007, 21:03:11) [GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)]
**System Platform** linux2
**SOFTWARE_HOME** /usr/lib/zope2.9/lib/python
**ZOPE_HOME** /usr/lib/zope2.9
**INSTANCE_HOME** /var/lib/zope2.9/instance/plone-site
**CLIENT_HOME** /var/lib/zope2.9/instance/plone-site/var
**Network Services** ZServer.HTTPServer.zhttp_server (Port: 8081)
Process Id 5505 (-1235932272)
Running For 5 min 47 sec

But when I try to access my plone-site with the URL that I used before upgrading to Feisty ([http://localhost:8081/plone-site)]("http://localhost:8081/plone-site%29"), I get the following error message:
*************
[SIZE=3]** Site Error**[/SIZE]
An error was encountered while publishing this resource.
**Resource not found**
Sorry, the requested resource does not exist.
Check the URL and try again.
**Resource: **plone-site GET
*********

[COLOR=Sienna]**Does anyone know what I'm doing wrong?**[/COLOR]

Thanks.

---

### Post by datakid on 2007-05-03
I can confirm this. 

I had a zope/plone site up from about a month ago at home, which was working fine. As I am only testing/teaching myself, I did a reinstall of zope/plone about a week ago to try some new add on products, and am now left with resource not found.

Have done extensive looking for problem, but am not a guru, so may have missed something.

The add on that I was installing was Quills. I presume it wouldn't be that?

---

### Post by ronb on 2007-05-04
I'm using Plone for testing and teaching myself also. And I also had a prior version up and running on Dapper. I went to Edgy last weekend and Zope and Plone quit working. I continued to upgrade to Feisty hoping that it might get fixed. It didn't.

I uninstalled Zope and Plone marking them for complete removal. Then I installed plone-site from Synaptic. And that's where I'm at now.

Other threads have mentioned that, after installing the software, you have to 'Add' a plone-site instance to Zope. I vaguely remember doing something like that the first time that I set it up, but I don't see where to do it with Zope version 2.9.

I don't know what Quills is, but you've got me curious. I'll check it out.

---

### Post by datakid on 2007-05-04
so, when you have fully installed zope, go to a browser, type in 

http:/localhost:8081/manage

and you will see the zope management interface. On the right hand side near the top you will see a drop down box and the "add" button next to it....drop it down, choose "plone site", bob's your mother's brother

---

### Post by ronb on 2007-05-05
Thanks.

---

