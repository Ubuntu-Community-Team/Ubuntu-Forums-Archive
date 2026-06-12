---
title: "Default repositories"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by gofishel on 2008-01-07
I upgraded from 7.04 to 7.10 and my sources still say feisty. Can someone post the default /etc/apt/sources.list so I can check it against mine?
Or how do I reset me repos back to the default?
Well I got one from the wiki but I still dont see a source repo for "ia32-libs-gtk" in synaptic package manager?

thanks

---

### Post by forestpixie on 2008-01-08
you can get yourself a sources.list from here

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

I assume you know how to edit the original

---

### Post by Sef on 2008-01-08
> I upgraded from 7.04 to 7.10 and my sources still say feisty. Can someone post the default /etc/apt/sources.list so I can check it against mine?
Or how do I reset me repos back to the default?

Go to System > About Ubuntu.   Does the second paragraph say this:

> Thank you for your interest in Ubuntu 7.10
                - the Gutsy Gibbon - released in October 2007.

If not, then you have not upgraded to Ubuntu 7.10 - Gutsy Gibbon.

---

### Post by forestpixie on 2008-01-08
> Thank you for your interest in Ubuntu 7.10
- the Gutsy Gibbon - released in October 2007.
If not, then you have not upgraded to Ubuntu 7.10 - Gutsy Gibbon.

mine says that and I have ?

---

### Post by zvacet on 2008-01-08
```
 sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list 
```

---

### Post by gofishel on 2008-01-08
Thanks, but ia32-libs-gtk still doesn't show any version in synaptic package manager

---

### Post by Partyboi2 on 2008-01-08
There doesn't seem to be ia32-libs-gtk for gusty
Is the package you wanting [I]ia32-libs? 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ia32-libs&searchon=all&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ia32-libs&searchon=all&subword=1&version=all&release=all)
[/I]

---

### Post by gofishel on 2008-01-08
Ah.. thanks for the quick reply.

Heres the story:
I have a 32 bit system and am trying to install the 32 bit firefox as per
<http://ubuntuforums.org/showthread.php?t=202537>
They say to install ia32-libs-gtk first.
 Ok, so now I skip that (because there is none for gutsy) and try to install  the firefox 32 package and, it complains it cant find ia32-lib-firefox

---

### Post by Partyboi2 on 2008-01-08
You can install it by going to add/remove listed under "Applications" and searching for firefox and installing it
or open a terminal
```
sudo apt-get install firefox
```
That how-to you are trying to use is for installing firefox 32bit onto a amd 64 bit machine.

---

### Post by gofishel on 2008-01-08
Opps.. I meant I have a 64 bit system

---

### Post by gofishel on 2008-01-08
SOLUTION:

I installed the package from post #8 from [http://ubuntuforums.org/showthread.php?t=574857](http://ubuntuforums.org/showthread.php?t=574857)
that installs all the 32 bit libs!

---

### Post by Partyboi2 on 2008-01-08
>  Download any of the browser deb files above. I totaly recommend Swiftweasel Then download the [ia32-lib-firefox-amd64]("http://home.comcast.net/%7Eubuntume/ia32-lib-firefox-amd64.deb") packages save them to your desktop.
Double click on ia32-lib-firefox and let Gedebi install it first then do the same with the browser deb you selected from above.
Did you do as the how-to mentioned and downloaded
[http://home.comcast.net/~ubuntume/ia32-lib-firefox-amd64.deb?](http://home.comcast.net/~ubuntume/ia32-lib-firefox-amd64.deb?)

---

### Post by gofishel on 2008-01-08
> **Partyboi2 said:**
> Did you do as the how-to mentioned and downloaded
[http://home.comcast.net/~ubuntume/ia32-lib-firefox-amd64.deb?](http://home.comcast.net/~ubuntume/ia32-lib-firefox-amd64.deb?)

yes

---

