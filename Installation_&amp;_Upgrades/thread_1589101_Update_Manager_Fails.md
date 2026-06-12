---
title: "Update Manager Fails"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by hewjr1000 on 2010-10-05
Installed Unbuntu 10.04.1 using wubi.  Have windows Vista 32 bit, install went fine, however when I try to use update manager it fails to download updates.

any idea why?

---

### Post by Chris1274 on 2010-10-05
A number of us have been having trouble with updates today. You might try this fix:

>  					Originally Posted by **coffeecat** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9929034#post9929034") 				
 				[I]
Go to System > Administration > Software Sources and under  "Download from" you can select the main server, your country or "other".  Choose other and you can select any you like from a very long list or  click on the 'Select Best Server' button.[/I]


---

### Post by tommcd on 2010-10-06
> **hewjr1000 said:**
> Installed Unbuntu 10.04.1 using wubi.  Have windows Vista 32 bit, install went fine, however when I try to use update manager it fails to download updates.

According to Wubi's developer Agostino Russo, Wubi was only meant as a way to try out Ubuntu. He never intended anyone to upgrade using Wubi:
> Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
> We are working on the ability to start with a Wubi installation and later upgrade that to a full installation within a dedicated partition.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
So if you have been using Ubuntu for a while with Wubi, it is time to do a real Ubuntu install to a dedicated partition on your hard drive. It will perform better that way also.

---

