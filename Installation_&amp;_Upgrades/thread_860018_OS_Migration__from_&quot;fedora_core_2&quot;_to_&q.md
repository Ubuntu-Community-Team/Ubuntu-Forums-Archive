---
title: "OS Migration : from &quot;fedora core 2&quot; to &quot;ubuntu 8&quot;"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by madmax1973 on 2008-07-15
Hi every Body :)

I'm going to migrate a server from "fedora core 2" to "ubuntu 8" ( don't now yet exctacly what's running over it !! i just know that there is "Repository" and a DB over it ) can any one help me, telling where to find documentation, or help with some suggestions and/or tips.

Thank you so much !

bye 

Mad Max

---

### Post by kunixos on 2008-07-15
the best place to start would be reading about the Ubuntu Server Edition [here]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

I'd figure out exactly WHAT it is you are using the fedora core server for and make an attempt at migrating the data to the new server. Also, you could try creating a separate partition for the /var directory so that later you can keep your files in tact without worry when you do decide to change server systems.

Ultimately it's a good switch, IMHO, because Core 2 is OLD (buggy, outdated, Fedora doesn't even use the core/extra model anymore, etc.) and Ubuntu provides really supurlative Long Term Support for their Server customers (you'd have to use Red Hat Enterprise to get the same support).

Hope this helps!

---

### Post by Pumalite on 2008-07-15
This is old, but gives an idea on how to set up a Server:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by madmax1973 on 2008-07-15
Thanks alot Kunixos, 

I'll read the doc over the link you gave me and according to what you wrote, i think that i have to attempt to clone the existing data under fedora on the Ubuntu server some how ! ( recreate the same hard disk copy of data over another machine, test server, with ubuntu as OS !! ) and see what will be going on, i mean how it works !!! 

what did you meant with : "creating a separate partition for the /var" to copy the data over that fs some where else ?!

---

