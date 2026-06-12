---
title: "ubuntu server connection"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by vaish05_s on 2011-03-28
Hi,
I'm trying to install packages from synaptic package manager from past a week (21st march 2011).
I get the following error for installation of packages like gstreamer bad plugins and ugly plugins.

**Unable to connect to in.archive.ubuntu**....some url like this

I also did apt-get install(The cli version of the synaptic manager) and i get the same error
I ran that url thru browser and the connection to server timed out.
Is the ubuntu server down??
Can you suggest other alternatives to download packages and install automatically instead of manually from tar files...

Thank you

---

### Post by sikander3786 on 2011-03-28
Welcome to the forums :-)

We need to see the complete output of following command please.

Applications > Accessories > Terminal:

```
sudo apt-get update
```

Also a few days ago, I heard that some problem was going on with the Indian servers so it is worth to try another mirror. Go to Applications > Software Center > Edit > Software Sources and choose 'Main' server for your downloads. What is the output then?

---

### Post by Sean Moran on 2011-03-28
> **vaish05_s said:**
> Hi,
I'm trying to install packages from synaptic package manager from past a week (21st march 2011).
I get the following error for installation of packages like gstreamer bad plugins and ugly plugins.

**Unable to connect to in.archive.ubuntu**....some url like this

I also did apt-get install(The cli version of the synaptic manager) and i get the same error
I ran that url thru browser and the connection to server timed out.
Is the ubuntu server down??
Can you suggest other alternatives to download packages and install automatically instead of manually from tar files...

Thank you
I guess by the 'in.archive.ubuntu...' that you're set to go with the in. server.  I wouldn't know whether that's for INdia or INdonesia, but the same solution applies.  Goto System->Administration->Software Sources and on the first main tab, you will see the DOWNLOAD FROM: selection bar.

Select Main Server.  

That should help to determine if the problem is at the other end, or your end.  It might be that your own connection is not running 100%, but change the Software Sources to the Main Server, just to test it out, and hopefully you'll have more luck that I get when I try to download packages from the Burkina Faso (bf) server, which isn't 100% reliable nor always updated at the latest hour.

---

