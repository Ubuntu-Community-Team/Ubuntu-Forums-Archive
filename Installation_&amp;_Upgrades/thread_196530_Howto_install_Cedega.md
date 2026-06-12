---
title: "Howto install Cedega????"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by Matthewrd on 2006-06-14
Does anyone out there use cedega? If you do hopefully you were able to install it on Ubuntu 6.06 Dapper Drake when I try to install the deb file with Gdebi I get dependencies errors the one I'm stuck on now is xlibs in synaptic it says it is installed. I'm not a Linux expert by any means more like newb so a newb answer would be the best, if anyone can. If the way I must do this in the terminal ill need step by step instructions I feel so dumb but I bought this software and it says it prefers debian based distros so i hope this isn't one of those debs that don't work with ubuntu. i only spent 15 USD on the program so I just want to at least install it. lol. If I'm lucky maybe there's a repository out there with Cedega on I don't know so any help would be appreciated. Of course I know my way around synaptic well so I was hoping the whole time I could use synaptic to install it but since I had to buy it I don't think ill be able too. Hopefully someone will have some kind of answer for me thank you for reading my post and thank you even more for replying with an answer.
Thank You
Matthew

---

### Post by frodon on 2006-06-14
Here is the answer : [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)

---

### Post by PsYsK8eR on 2006-06-17
[QUOTE=frodon]Here is the answer : [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)[/QUOTE]

The problem is, this is a workaround that is time consuming, because everytime a ".deb" package is missing "xlibs" you'll have to edit the package.

In dapper (ubuntu 6.06) "xlibs" changed, and it cannot be recognized by (older) ".deb" installation packages, making it impossible to install one of those packages.

The solution to this is installing a "dummy package", which i have attached to this reply.

good luck!

---

### Post by tokez on 2006-06-20
you can go to [http://www.ubuntuforums.org/showthread.php?p=1124425](http://www.ubuntuforums.org/showthread.php?p=1124425) for a compile script that will install cedega cvs. i tested it on dapper 6 and it works

---

