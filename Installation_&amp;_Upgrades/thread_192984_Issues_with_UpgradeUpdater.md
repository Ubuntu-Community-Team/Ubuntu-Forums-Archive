---
title: "Issues with Upgrade/Updater"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by Fleaman13 on 2006-06-09
Hello all, I am having some issues when I upgrade. I get a pop-up that says this... 
"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found"

Thanks in advance for any help.

---

### Post by tonyr on 2006-06-09
My first impression is that it is exactly what it says:  There is a network problem
somewhere.  The web pages that the updater is trying to access may be unavailable
for some reason.  

I just checked to see if those URLs existed, and they do not.  You need to find some
other repositories for the packages you are interested in, or other methods
of download/installation.

---

### Post by Fleaman13 on 2006-06-09
Those are the URL's that came along with the original install... have they been updated? If so where can I find them?

Thanks.

---

### Post by FredB on 2006-06-09
[QUOTE=Fleaman13]Hello all, I am having some issues when I upgrade. I get a pop-up that says this... 
"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found[/quote]

When I come to [http://theli.free.fr/packages/]("http://theli.free.fr/packages/") I can see :

```

[DIR] _breezy_obsoltete/      20-Mar-2006 00:56      -  
[DIR] dapper/                 08-May-2006 16:39      -  
[DIR] debsource/              17-Mar-2006 14:35      -  
[DIR] src/ 

```

No more breezy support !

> 
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found"


When I go to this address, I can only see :

```

[DIR] artwork/                
[DIR] img/                      
[DIR] scripts/  

```

--> Dead link.

> 
Thanks in advance for any help.

So, you will have to upgrade to dapper if you still want to use Listen. Sorry to say it this way !

---

### Post by jfl on 2006-06-09
I have exactly the same problem; will try again later and keep you posted if it works...

---

